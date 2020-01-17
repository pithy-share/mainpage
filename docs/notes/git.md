# git

## Set up

[git setup](https://git-scm.com/)

## Base

### clone

```bash
git clone https://github.com/zyongzhangyong/cauto.git
```

### status

```bash
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   docs/myproj/bmp.md
        modified:   mkdocs.yml
```

### add

```bash
$ git add docs/notes/git.md
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   docs/notes/git.md
```

### commit

```bash
$ git commit -m "add git usage"
[master 564d7bc] add git usage
 1 file changed, 14 insertions(+)
 create mode 100644 docs/notes/git.md

```

### push

```bash
$ git push
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 4 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 628 bytes | 628.00 KiB/s, done.
Total 5 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/zyongzhangyong/mainpage.git
   eaea8e7..564d7bc  master -> master

```

### reset
* soft reset

not clean your modify 
```shell
git reset --soft 97ef9812b55cf14680eb8b70a39fb4821abb54dd
```

* hard reset

clean your modify 
```shell
git reset --hard 97ef9812b55cf14680eb8b70a39fb4821abb54dd
```


## Branch

### view
```bash
	$ git branch
	* master
```

### create

```bash
$ git branch test
Administrator@PC-20180827CUXX MINGW64 /e/git_rep/github/mainpage/mainpage (master)
$ git branch
* master
  test
```
### switch
```bash
$ git branch
* master
  test

Administrator@PC-20180827CUXX MINGW64 /e/git_rep/github/mainpage/mainpage (master)
$ git checkout test
Switched to branch 'test'
M       docs/myproj/bmp.md
M       docs/notes/git.md
M       mkdocs.yml

Administrator@PC-20180827CUXX MINGW64 /e/git_rep/github/mainpage/mainpage (test)
$ git branch
  master
* test
```

### del
```bash
$ git checkout master
Switched to branch 'master'
M       docs/myproj/bmp.md
M       docs/notes/git.md
M       mkdocs.yml
Your branch is up to date with 'origin/master'.

$ git branch
* master
  test

Administrator@PC-20180827CUXX MINGW64 /e/git_rep/github/mainpage/mainpage (master)
$ git branch -d test
Deleted branch test (was 564d7bc).

Administrator@PC-20180827CUXX MINGW64 /e/git_rep/github/mainpage/mainpage (master)
$ git branch
* master
```

## Add ssh key

### view
* if has no ssh key, to `create`
* if has ssh key, to `add pubkey to github`
```bash
$ ls ~/.ssh/
id_rsa  id_rsa.pub  known_hosts
```


### create

```bash
ssh-keygen -t rsa -C "your_email@example.com"
```

### add pubkey to github

1.copy pulic key to clipboard

```bash
clip < ~/.ssh/id_rsa.pub
```

2.click setting

![setting.img](../img/github_setting.jpg)

3.click `New SSH key`

![ssh.img](../img/github_ssh.jpg)

4.copy string from clipboard and add

![sshstring.img](../img/github_ssh_copy.jpg)

### test ssh key
```bash
$ ssh -T git@github.com
The authenticity of host 'github.com (13.250.177.223)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
```
input `yes`
```bash
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com,13.250.177.223' (RSA) to the list of known hosts.
Hi zyongzhangyong! You've successfully authenticated, but GitHub does not provide shell access.
```


### clone Repositories with ssh

![clonessh.img](../img/github_clonessh.jpg)

## Other

### init

```bash
mkdir myrep
cd myrep
git init
```

### view remote repository version 

```bash
$ git remote -v
origin  git@github.com:zyongzhangyong/mainpage.git (fetch)
origin  git@github.com:zyongzhangyong/mainpage.git (push)
```

### ignore file

```bash
touch .gitignore
```

add ignore files or dir in .gitignore

```bash
site/*
*.log
```

### view log or diff

```bash
gitk
```

![gitk.img](../img/gitk.jpg)

