# Linux

## Basic things to know for Linux:

-   To get a repo list for Fedora:
```bash
sudo dnf repolist
```

-   To update Fedora:

```bash
sudo dnf  full-upgrade -y
```

-   To Install the dnf-plugin-system-upgrade package:

```bash
sudo dnf install dnf-plugin-system-upgrade
```

-   To download updated packages (version 36):
```bash
sudo dnf system-upgrade download --releasever=36
```

## How to install Tools List

We can make a file in the terminal by typing:
```bash 
nano tools.list
```

From there we can paste or type in the names of tools we want to install. In my case I decided to install:
git
vim
tmux

```bash
[c0rnkrump3t@fedora ~]$ sudo dnf install $(cat tools.list | tr "\n" " ") -y
[sudo] password for c0rnkrump3t: 
Last metadata expiration check: 1:05:29 ago on Wed 01 Jun 2022 07:32:35 PM.
Package git-2.36.1-1.fc36.x86_64 is already installed.
Package tmux-3.2a-3.fc36.x86_64 is already installed.
Dependencies resolved.
===================================================================================
 Package                             Architecture                Version                                  Repository                    Size
===================================================================================
Installing:
 vim-enhanced                        x86_64                      2:8.2.4975-1.fc36                        updates                      1.9 M
Installing dependencies:
 gpm-libs                            x86_64                      1.20.7-40.fc36                           fedora                        21 k
 libsodium                           x86_64                      1.0.18-9.fc36                            fedora                       163 k
 vim-common                          x86_64                      2:8.2.4975-1.fc36                        updates                      7.0 M
 vim-filesystem                      noarch                      2:8.2.4975-1.fc36                        updates                       22 k

...SNIP...

Installed:
  gpm-libs-1.20.7-40.fc36.x86_64                libsodium-1.0.18-9.fc36.x86_64                  vim-common-2:8.2.4975-1.fc36.x86_64        
  vim-enhanced-2:8.2.4975-1.fc36.x86_64         vim-filesystem-2:8.2.4975-1.fc36.noarch        

Complete!

```

We can see that git and tmux were already installed, however vim was not. 

#### Good to know:
If any of the tools don’t work anymore or can't be installed through a tools list, and you try to run the command, it will not work. Make sure to remove all the tools that are giving you errors. 