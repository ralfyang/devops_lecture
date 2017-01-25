# DevOps Lecture document
## Make a Dev. environment on laptop(Linux or MacBook)
### User Base environment Setup - Text color changes with Command Alias

```sh
cat << EOF >>  ~/.bash_profile
alias ll='ls -lai'
export CLICOLOR=1
export LSCOLORS=GxFxCxDxBxegedabagaced
export TERM="xterm-color" 
export PS1='\[\e[0;33m\]\u\[\e[0m\]@\[\e[0;32m\]\h\[\e[0m\]:\[\e[0;34m\]\w\[\e[0m\]\$ '
EOF
```

### Key-gen for public/ private key
```sh
ssh-keygen -t rsa -b 4096
```

### Check the public-key
```sh
cat ~/.ssh/id_rsa.pub
```

## Git
### How to use Github
#### Add a public key to Github profile setting
* Copy your Public-key as below
```sh
cat ~/.ssh/id_rsa.pub
```

* Paste the public-key to here 
    * https://github.com/settings/profile
    * SSH and GPG keys > SSH keys > "New SSH Key"


## Tools
### docker-compose: https://docs.docker.com/compose/install
#### How to install and use
* Install
```sh
$ curl -L "https://github.com/docker/compose/releases/download/1.10.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

### gitpush auto: https://github.com/goody80/gitpush_direct
#### How to install and use
* Install
```sh
curl -sL bit.ly/gitauto |bash
```

* Use
```sh
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
```sh
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
```sh
curl -sL bit.ly/ralf_dcs -o ./dcs
sudo chmod 755 ./dcs
sudo mv ./dcs /usr/bin/dcs
```


## Docker Dev. env.
### Docker environment via virtual box with vagrant
#### Git document
* https://github.com/goody80/vagrant_docker_cluster
```sh
git clone https://github.com/goody80/vagrant_docker_cluster.git
cd vagrant_docker_cluster
vi Vagrantfile
vagrant up docker01.dev
vagrant ssh docker01.dev
```



## Rancher Dev. env.
### Rancher via virtual box with vagrant
#### Git document
* https://github.com/goody80/vagrant_rancher_cluster
```sh
git clone https://github.com/goody80/vagrant_rancher_cluster.git
cd vagrant_rancher_cluster
vagrant up rancher && vagrant up vmhost01  && vagrant up vmhost02
```

