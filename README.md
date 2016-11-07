# Welcome to my dotfiles

Each folder contains application related dotfiles with any related dotfiles/files that you may need during setup. This will mimic some of my local dev environment but not all; however, I am working to put more and more of my own environment into this repo.
  

# README.md file structure
```
⋅⋅H2 - {Github folder name}
⋅⋅⋅H3 - {file name inside Github folder name}
```

**H2** -- Github folder and the section will provide context how to setup your own enironment with that particular application.

**H3** -- Subheader providing context around a particular dotfile or file in directory you are in.


## tmux

symlink your `.tmux.conf` file to a home `.tmux.conf` file. You do not need to create the configuration file you are symlinking to, it will just happen.

```
$ ln -s /absolute/path/to/dir/.tmux.conf ~/.tmux.conf
```

symlink your `tmuxcmds` directory and all of its contents.

```
$ ln -s /absolute/path/to/dir/* ~/tmuxcmds/
```

run this command again whenever you create a new tmux command inside of th `tmuxcmds` directory. This will create a new symbolic link for any new file it finds inside `tmuxcmds`.

### ssh-multi.sh

This is a bash script to ssh into many tunnels that will create as many panes as ssh tunnels you specify.

alias ssh-multi.sh in your `.bash_profile` or `.bashrc`

*if you follow the instructions above, this will be the path you want to specify inside your .bash file*

```sh
alias mssh="~/tmuxcmds/ssh-multi.sh"
```

Depending on where you placed your alias, you will need to source that .bash file.

```
$ source .bash_profile
```
**or**
```
$ source .bashrc
```

I would create a `config` file inside your `~/.ssh` directory that would have aliases for servers you usually tunnel into.

```
host {aliasCommand}
        HostName {serverName}
        User {yourUserName}
```

Run alias command `mssh`.

```
$ mssh
```

You should get a prompt
```
$ Please provide a list of hosts (separated by spaces) [ENTER]: 
```

List your servers using `host` name you specified in `config` file of `~/.ssh` with spaces and hit ENTER. This will create a speate tmux session with your ssh tunnels.