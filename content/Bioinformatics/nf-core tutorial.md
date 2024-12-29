---
author: Harvey Guo
created: 2024-12-25 20:07
modified: 2024-12-25 20:07
aliases: []
share: true
---
## 使用Slurm调度作业
### 升级Slurm（建议）
Slurm默认的资源选择是以节点为粒度的资源分配（select/linear），在节点中如果作业申请资源不能全部占满全部核心，就会出现资源超额分配的问题。也就是在实际运行中，一个节点只能同时运行一项任务，无法做到一个节点同时运行多项任务。
>独占模式调度策略的优势在于，作业可以获得所分配节点的全部资源，从而实现最佳的并行性能。其缺点是，作业可能会占用大量其自身并不使用的资源，而这些资源也无法与其他作业共享。

Slurm在19.05的版本中，增加了_cons_tres_ Select 插件，可以做到将单个的CPU核、内存、GPU及其它可追踪资源作为可消费资源（消费及分配）。也就是可以根据每项任务所需求的CPU核、内存、GPU数量，将其填充到节点中，做到一个节点中同时运行多个任务，最大化利用资源。
>消耗型资源调度策略的优势在于可以显著提升作业吞吐量。集群的整体作业吞吐量和生产力得以提高，从而减少用户等待作业完成的时间，并提升集群的整体使用效率。其缺点是，默认情况下，用户无法独占整个节点来运行其作业。

目前服务器上Slurm版本为18.08.8，没有_cons_tres_ Select 插件，需要升级到新版本。（目前有_cons_res_ Select插件，但只能将单个的CPU核和内存作为可消费资源，无法细致管理GPU，并且不支持_cons_tres_的许多功能）
### 升级教程
参考
- [升级slurm，从18.08到23.02 - 花花今天没吃药 - 博客园](https://www.cnblogs.com/HuaNeedsPills/p/17968536)
- [Slurm Workload Manager - Upgrade Guide](https://slurm.schedmd.com/upgrades.html#preparation)
注意升级时不能一次超过两个大版本，因此需要逐步升级。如上面教程的策略是18.08->20.02->21.08->23.02
### 修改slurm.conf
修改SelectType=SELECT/LINEAR为
```
SelectType=select/cons_tres
SelectTypeParameters=CR_Core_Memory
```
可选但建议增加DefMemPerCPU，即默认为每个线程配备的内存量，防止memory oversubscription
```bash
# Based on 256GB nodes
# 256GB * 0.95 = 243GB usable 
# 243GB * 1024 / 64 ≈ 3,888MB
DefMemPerCPU=3888
```

>[!tip] 
>可在提交任务时使用`--mem-per-cpu=`覆盖此参数

详细解释：
- [Slurm Workload Manager - Consumable Resources in Slurm](https://slurm.schedmd.com/cons_tres.html)
- [Slurm Workload Manager - Sharing Consumable Resources](https://hpc.rz.rptu.de/documentation/cons_res_share.html)
### Parallelization

When submitting parallel code, you usually need to specify the number of tasks, nodes, and CPUs to be used by your job in various ways. For any given use case, there are generally multiple ways to set the options to achieve the same effect; these examples try to illustrate what we consider to be best practices.

The key options for parallelization are:

- `--nodes` (or `-N`): indicates the number of nodes to use
- `--ntasks-per-node`: indicates the number of tasks (i.e., processes one wants to run on each node)
- `--cpus-per-task` (or `-c`): indicates the number of cpus to be used for each task

In addition, in some cases it can make sense to use the `--ntasks` (or `-n`) option to indicate the total number of tasks and let the scheduler determine how many nodes and tasks per node are needed. In general --cpus-per-task will be 1 except when running threaded code.  

Note that if the various options are not set, SLURM will in some cases infer what the value of the option needs to be given other options that are set and in other cases will treat the value as being 1. So some of the options set in the example below are not strictly necessary, but we give them explicitly to be clear.

Here's an example script that requests an entire Savio3 node and specifies 32 cores per task.

    `#!/bin/bash     #SBATCH --job-name=test     #SBATCH --account=account_name     #SBATCH --partition=savio3     #SBATCH --nodes=1     #SBATCH --ntasks-per-node=1     #SBATCH --cpus-per-task=32     #SBATCH --time=00:00:30     ## Command(s) to run:     echo "hello world"`

Only the partition, time, and account flags are required.


# Other
- https://docs-research-it.berkeley.edu/services/high-performance-computing/user-guide/running-your-jobs/submitting-jobs/#email-options