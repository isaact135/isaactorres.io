---
title: "How to Install Docker on Ubuntu"
date: 2021-03-01T11:57:18-08:00
draft: false
toc: false
images:
tags:
  - docker
---
Today, I will show you how to install Docker on Ubuntu. So you heard of something called "Docker". Everybody says containers are the future. You want to give it a shot. So lets get started with installing it.

The first thing your going to want to do is install system updates, You can do that by running this command:

    sudo apt update && sudo apt upgrade

Alright, now that your system is up to date we need to install a few packages

    sudo apt-get install \
      apt-transport-https \
      ca-certificates \
      curl \
      gnupg-agent \
      software-properties-common

After that finishes you need to get dockers official GPG Key

    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

And Then verify the fingerprint

    sudo apt-key fingerprint 0EBFCD88

Your output should look something like this:

    pub   rsa4096 2017-02-22 [SCEA]
          9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
    uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
    sub   rsa4096 2017-02-22 [S]

Now we can finally add the repository

    sudo add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) \
       stable"

Update you Repo's one more time

    sudo apt update

Now we can actually installed docker

    sudo apt-get install docker-ce docker-ce-cli containerd.io

To verify it is properly working run this

    sudo docker run hello-world

If you see the message you correctly installed docker

You can stop here or you can do these optional but highly recommended steps.

The first one is to add your user account to the docker group so you do not need to preface each command with sudo you can do that using this command

    sudo usermod -aG docker $USER

You might need to log out or reboot for change to take affect

The Last one is if you want docker to always run at startup this one is done by:

    sudo systemctl enable docker

or is you prefer not to have it running at start you can manually start it using:

    sudo systemctl start docker

Congrats you got installed now you can use docker to play around and learn more about containers.

If you want to want 100 dollars towards a VPS to play around with docker check out Linode. By using my link you get the free credit and It helps me earn credit on Linode too.

[Get my Free $100 Dollar Credit](https://www.linode.com/?r=3f2297c7b8ad8993172d73670a352dfda21bb833)
