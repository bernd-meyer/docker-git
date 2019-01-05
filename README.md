# docker-git

A small git container that makes you independent of local git installations.

---

## Usage

```
docker run --rm -it --user $(id -u ${USER}) -v $(pwd):/git -v ~/.ssh:/home/git/.ssh:ro bemede/git <git_command>
```

## Example

```
docker run --rm -it --user $(id -u ${USER}) -v $(pwd):/git -v ~/.ssh:/home/git/.ssh:ro bemede/git version
```
