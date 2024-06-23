---
author: Harvey Guo
created: 2023-08-12 20:07
modified: 2023-08-12 20:07
aliases: Untitled
share: true
---
Introduction:
In today's fast-paced digital world, efficient internet connectivity is crucial for smooth workflow and seamless browsing. However, there are times when we need to switch between using a proxy server and connecting directly to the internet. To simplify this process, we can create a bash tool in the .bashrc file. This tool allows us to easily turn on and off the proxy settings with just a few simple commands. In this blog post, we will guide you through the process of creating and using this bash tool.

Setting up the Bash tool:
To get started, open your favorite text editor and navigate to your home directory. Look for the .bashrc file. If it doesn't exist, create a new file with that name. Add the following code to the .bashrc file:

```bash
function proxy(){
 export HTTP_PROXY=http://your.proxy
 export HTTPS_PROXY=http://your.proxy
 # echo the proxy to ~/.wgetrc
 echo "http_proxy = http://your.proxy
 https_proxy = http://your.proxy
 use_proxy = on
 " > ~/.wgetrc
 echo "[https]
 	proxy = http://your.proxy
 [http]
 	proxy = http://your.proxy" >> ~/.gitconfig
}

function noproxy(){
 unset {HTTP,HTTPS}_PROXY
 echo "" > ~/.wgetrc
 sed -i '/\[https\]/,+3d' ~/.gitconfig
}
```

Explanation:
- The `proxy()` function sets the HTTP_PROXY and HTTPS_PROXY environment variables to the desired proxy server address. It also updates the ~/.wgetrc file  and ~/.gitconfig file with the proxy settings.
- The `noproxy()` function unsets the HTTP_PROXY and HTTPS_PROXY environment variables and clears the ~/.wgetrc file and ~/.gitconfig file .

Save the .bashrc file and exit the text editor.

Applying Changes:
To apply the changes made in the .bashrc file, either restart your terminal or run the following command:

```bash
source ~/.bashrc
```

Using the Bash Tool:
Now that we have set up the bash tool, let's see how easy it is to turn the proxy on and off.

To enable the proxy, simply enter the following command in your terminal:

```bash
$ proxy
```

This will set the proxy server address and update the ~/.wgetrc file.

To disable the proxy and connect directly to the internet, use the following command:

```bash
$ noproxy
```

This command will unset the proxy environment variables and clear the ~/.wgetrc file.
