# JVM - Julia version management (experimental)

**This is a project still in experimental stage. Many syntax and notations are not standardized yet. Use with care.**
**There are many things to be fixed as I am not good in writing shell script. Comments are welcome.**

Objectives: Inspired from `jill.sh`, `jill.py`, and `nvm-sh`. A possible realization to management Julia versions.

Why? Julia is a fast evolving language. It might be good to provide a way for developers to test their codes locally for various versions. Or perhaps users are eagear to try new versions, e.g., rc or beta. 

What the script will do? In .jvmrc, various environment variables can be found 
- `jvm` will download all the jua binaries`JULIA_DOWNLOAD_DIR`, which is set as `$HOME/Downloads/julia/` by default
    - `jvm download`
    - `jvm install`
- `jvm` will extract the binaries to `$JULIA_INSTALL_DIR`, which is set as `$HOME/apps/julia/` by defaut. 
    - `jvm install`
    - `jvm remove`
- `jvm` will manipulate symbolic links in `$JULIA_SYMLINK_DIR`, which is set as `$HOME/.local/bin` by defaut. Relevant operations are: 
    - `jvm load`
    - `jvm unload`
    - `jvm switch`
    - `jvm install`
- `jvm` tracks `$UPSTREAM_NAME` in `.jvmrc` file
-   - `jvm upstream`
- `jvm` will **not** touch your `.julia` folder. However, to migrate the `Project.toml` files between minor or major version, this might be necessary in future.


## Installation

1. Clone this repo in your prefered place such as `~/.jvm`   
2. Make it visible by appending `export PATH=$PATH:~/.jvm` to your shell rc file such as `~/.bashrc`, `~/.zshrc`
3. Make it executable, `chmod +x ~/.jvm/jvm`


## Basic usage

### Install/Installed
```shell
jvm install # Install the newest stable version from 
jvm install 1 # Install the newest major version 1
jvm install 1.5 # Install the newest major minor version 1.5
jvm install 1.5.3 # Install 1.5.3
jvm install 1.6.0 # Install 1.6.0, if not stable version exist, show rc version.
jvm install 1.6.0-rc1
jvm installed # list all installed version 
```

### Download
Download follows the same logic as install 

### Loaded/Load/Unload/Switch/Purge
```
jvm loaded # list all loaded symbolic link
jvm load 1.4.2 # make julia-1.4.2 available
jvm unload 1.4.2 # make julia-1.4.2 unavailable
jvm switch # switch the alias julia to a specific version
jvm purge # remove all symblic link except julia
```
### Status (incomplete)
formatting not done yet
```
jvm status # List all relevant information such as installed, loaded, upstream, downloaded
```
### Avail
```
jvm available # list all possible version from remote
jvm avail 
```

### Search 
```
jvm search 1
jvm search 1.1
jvm search 1.2
```


### nightly 
```
jvm nightly # Install the nightly version 
```
### Update (Not implemented yet)
Update jvm itself?
```
jvm update
```

## Relevant repos
- [jill.sh](https://github.com/abelsiqueira/jill)
- [jill.py](https://github.com/johnnychen94/jill.py)
- [nvm-sh](https://github.com/nvm-sh/nvm)
