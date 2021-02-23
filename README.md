# JVC - Julia version control (experimental)

**This is a project still in experimental stage. Many syntax and notations are not standardized yet. Use with care.**
**There are many things to be fixed as I am not good in writing shell script. Comments are welcome.**


Objectives: Inspired from `jill.sh`, `jill.py`, and `nvm-sh`. A possible realization to manage Julia versions.

Why? Julia is a fast evolving language. It might be good to provide a way for developers to test their codes locally for various versions. Or perhaps users are eagear to try new versions, e.g., rc or beta. 

What the script will do? In .jvcrc, various environment variables can be found 
- `jvc` will download all the jua binaries`JULIA_DOWNLOAD_DIR`, which is set as `$HOME/Downloads/julia/` by default
    - `jvc download`
    - `jvc install`
- `jvc` will extract the binaries to `$JULIA_INSTALL_DIR`, which is set as `$HOME/apps/julia/` by defaut. 
    - `jvc install`
    - `jvc remove`
- `jvc` will manipulate symbolic links in `$JULIA_SYMLINK_DIR`, which is set as `$HOME/.local/bin` by defaut. Relevant operations are: 
    - `jvc load`
    - `jvc unload`
    - `jvc switch`
    - `jvc install`
- `jvc` tracks `$UPSTREAM_NAME` in `.jvcrc` file
-   - `jvc upstream`
- `jvc` will **not** touch your `.julia` folder. However, to migrate the `Project.toml` files between minor or major version, this might be necessary in future.


## Installation

1. Clone this repo in your prefered place such as `~/.jvc`   
2. Make it visible by appending `export PATH=$PATH:~/.jvc` to your shell rc file such as `~/.bashrc`, `~/.zshrc`
3. Make it executable, `chmod +x ~/.jvc/jvc`


## Basic usage

### Install/Installed
```shell
jvc install # Install the newest stable version from 
jvc install 1 # Install the newest major version 1
jvc install 1.5 # Install the newest major minor version 1.5
jvc install 1.5.3 # Install 1.5.3
jvc install 1.6.0 # Install 1.6.0, if not stable version exist, show rc version.
jvc install 1.6.0-rc1
jvc installed # list all installed version 
```

### Download
Download follows the same logic as install 

### Loaded/Load/Unload/Switch/Purge
```
jvc loaded # list all loaded symbolic link
jvc load 1.4.2 # make julia-1.4.2 available
jvc unload 1.4.2 # make julia-1.4.2 unavailable
jvc switch # switch the alias julia to a specific version
jvc purge # remove all symblic link except julia
```
### Status (incomplete)
formatting not done yet
```
jvc status # List all relevant information such as installed, loaded, upstream, downloaded
```
### Avail
```
jvc available # list all possible version from remote
jvc avail 
```

### Search 
```
jvc search 1
jvc search 1.1
jvc search 1.2
```


### nightly 
```
jvc nightly # Install the nightly version 
```
### Update (Not implemented yet)
Update jvc itself?
```
jvc update
```

## Relevant repos
- [jill.sh](https://github.com/abelsiqueira/jill)
- [jill.py](https://github.com/johnnychen94/jill.py)
- [nvm-sh](https://github.com/nvm-sh/nvm)
- [IonCLI.jl](https://github.com/Roger-luo/IonCLI.jl)
