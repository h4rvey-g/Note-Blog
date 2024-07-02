---
author: Harvey Guo
created: 2024-06-30 21:08
modified: 2024-06-30 21:08
aliases: []
share: true
---
Run this in shell:
```bash
echo 'if (interactive() && Sys.getenv("RSTUDIO") == "") {
  source(file.path(Sys.getenv(if (.Platform$OS.type == "windows") "USERPROFILE" else "HOME"), ".vscode-R", "init.R"))
}' >> ~/.Rprofile
```
Or run this in R so it can immediately solve the problem in current R session:
```R
# Add text to ~/.Rprofile
writeLines('if (interactive() && Sys.getenv("RSTUDIO") == "") {
  source(file.path(Sys.getenv(if (.Platform$OS.type == "windows") "USERPROFILE" else "HOME"), ".vscode-R", "init.R"))
}', con = "~/.Rprofile")

# Source ~/.Rprofile
source("~/.Rprofile")
```

Reference: https://github.com/REditorSupport/vscode-R/issues/1094#issuecomment-1118440502