# docker-git

A small git container that makes you independent of local git installations.

---

## Usage

```
docker run --rm -it --user <uid> -v <working directory>:/git -v <path to .ssh subdirectory>:/home/git/.ssh:ro bemede/git <git_command>
```




## Example

```
docker run --rm -it --user $(id -u ${USER}) -v $(pwd):/git -v ~/.ssh:/home/git/.ssh:ro bemede/git clone git@github.com:bernd-meyer/docker-git.git
```
This command bind mounts
- the working directory in the containers */git* directory
- your *.ssh* subdirectory in the *.ssh* subdirectory of the container default user, the latter directory with read only permissions.

It sets the uid of the container default user ("git") to your uid so that
- the container default user has read permission on your .ssh files
- you are the owner of all created files and directories (e.g. after clone or pull)

The specified repository gets cloned into the bind mounted working directory. 

## Alias

Create an alias to invoke that command by a shortcut for your convenience, instead of repeatetly typing the command sequence.

In Bash you add the following line to file *~/.bash_aliases* (if it does not exist, create it)
```
alias git='docker run --rm -it --user $(id -u ${USER}) -v $(pwd):/git -v ~/.ssh:/home/git/.ssh:ro bemede/git'
```

To execute the command shown in the example above you now simply run the alias
```
git clone git@github.com:bernd-meyer/docker-git.git
```

