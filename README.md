# DevOps Lecture document
## Make a Dev. environment on laptop(MacBook)
### User Base environment Setup - Text color changes with Command Alias
```
cat << EOF >>  ~/.bash_profile
alias ll='ls -lai'
export CLICOLOR=1
export LSCOLORS=GxFxCxDxBxegedabagaced
export TERM="xterm-color" 
export PS1='\[\e[0;33m\]\u\[\e[0m\]@\[\e[0;32m\]\h\[\e[0m\]:\[\e[0;34m\]\w\[\e[0m\]\$ '
EOF
```

### Key-gen for public/ private key
```
ssh-keygen -t rsa -b 4096
```

### Check the public-key
```
cat ~/.ssh/id_rsa.pub
```

## Git
### How to use Github
#### Add a public key to Github profile setting
* Copy your Public-key as below
```
cat ~/.ssh/id_rsa.pub
```

* Paste the public-key to here 
    * https://github.com/settings/profile
    * SSH and GPG keys > SSH keys > "New SSH Key"


## Tools
### gitpush auto: https://github.com/goody80/gitpush_direct
#### How to install and use
* Install

```
curl -sL bit.ly/gitauto |bash
```

* Use

```
==================================================================
 -  Install has been completed  -                  Version 0.2
==================================================================
 You just can use
    $ gitpush
 or
    $ gitpush [COMMENT for commit]

 One more thing. 'gitpush-brach' for branch commit!!

 Enjoy!! :)
==================================================================
```

* Source

```
$ cat /usr/local/bin/gitpush
#!/bin/bash
### Made by Ralf Yang
### goody80762@gmail.com
ver=0.2 ## Version

Commit_comment=$@
User_editor='vim'
Core_editor=`git config --list |grep "core.editor" | awk -F '=' '{print $2}'`
	if [[ $Core_editor != '$User_editor'  ]];then
		git config --global core.editor $User_editor
	fi

git pull
git add *; git status

echo ""
echo "==========================================================================="
echo " Please push the Enter key if you confirmed or \"n\" for stop [Enter / n] "
echo "==========================================================================="
echo ""
read touch1
	if [[ $touch1 = "n" ]];	then
		echo " You just stopped the git upload..."
		exit 0;
	fi

	if [[ $Commit_comment = "" ]];then
		git commit
	else
		git commit -m "$Commit_comment"
	fi

git push -u origin master
```

### Docker Cli-dashboard: https://github.com/goody80/docker_cli_dashboard
#### How to install and use
* Install 
```
curl -sL bit.ly/ralf_dcs -o ./dcs
sudo chmod 755 ./dcs
sudo mv ./dcs /usr/bin/dcs
```


## Rancher Dev. env.
### Rancher via virtual box with vagrant
#### Git document
* https://github.com/goody80/vagrant_rancher_cluster


