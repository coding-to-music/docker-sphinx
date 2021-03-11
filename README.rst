docker-sphinx
=================

Here is the directory structure.::

    connorstom@penguin:~/aprojects/coding-to-music.github.io$ tree -d -L 2
    .
    ├── docs
    │   ├── build
    │   ├── source
    ├── images
    └── ver3.7
        ├── bin
        ├── include
        ├── lib
        ├── lib64 -> lib
        └── share



Installing Docker.::Python

    connorstom@penguin:~/aprojects/coding-to-music.github.io$ tree -d -L 2
    .
    ├── docs
    │   ├── build
    │   ├── source
    ├── images
    └── ver3.7
        ├── bin
        ├── include
        ├── lib
        ├── lib64 -> lib
        └── share


    (ver3.7) connorstom@penguin:~$ sudo apt-get install \
    >     apt-transport-https \
    >     ca-certificates \
    >     curl \
    >     gnupg \
    >     lsb-release
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    apt-transport-https is already the newest version (1.8.2.2).
    curl is already the newest version (7.64.0-4+deb10u1).
    gnupg is already the newest version (2.2.12-1+deb10u1).
    gnupg set to manually installed.
    The following additional packages will be installed:
    distro-info-data
    Suggested packages:
    lsb
    The following NEW packages will be installed:
    distro-info-data lsb-release
    The following packages will be upgraded:
    ca-certificates
    1 upgraded, 2 newly installed, 0 to remove and 30 not upgraded.
    Need to get 200 kB of archives.
    After this operation, 98.3 kB of additional disk space will be used.
    Do you want to continue? [Y/n] y
    Get:1 https://deb.debian.org/debian buster/main amd64 ca-certificates all 20200601~deb10u2 [166 kB]
    Get:2 https://deb.debian.org/debian buster/main amd64 distro-info-data all 0.41+deb10u3 [6,640 B]
    Get:3 https://deb.debian.org/debian buster/main amd64 lsb-release all 10.2019051400 [27.5 kB]
    Fetched 200 kB in 1s (353 kB/s)   
    debconf: delaying package configuration, since apt-utils is not installed
    (Reading database ... 46825 files and directories currently installed.)
    Preparing to unpack .../ca-certificates_20200601~deb10u2_all.deb ...
    Unpacking ca-certificates (20200601~deb10u2) over (20190110) ...
    Selecting previously unselected package distro-info-data.
    Preparing to unpack .../distro-info-data_0.41+deb10u3_all.deb ...
    Unpacking distro-info-data (0.41+deb10u3) ...
    Selecting previously unselected package lsb-release.
    Preparing to unpack .../lsb-release_10.2019051400_all.deb ...
    Unpacking lsb-release (10.2019051400) ...
    Setting up distro-info-data (0.41+deb10u3) ...
    Setting up ca-certificates (20200601~deb10u2) ...
    Updating certificates in /etc/ssl/certs...
    13 added, 4 removed; done.
    Setting up lsb-release (10.2019051400) ...
    Processing triggers for man-db (2.8.5-2) ...
    Processing triggers for ca-certificates (20200601~deb10u2) ...
    Updating certificates in /etc/ssl/certs...
    0 added, 0 removed; done.
    Running hooks in /etc/ca-certificates/update.d...
    done.
    (ver3.7) connorstom@penguin:~$ curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    (ver3.7) connorstom@penguin:~$ echo \
    >   "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
    >   $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    (ver3.7) connorstom@penguin:~$ sudo apt-get update
    Get:1 https://download.docker.com/linux/debian buster InRelease [44.4 kB]
    Ign:2 https://storage.googleapis.com/cros-packages/88 buster InRelease                                                                          
    Hit:3 https://storage.googleapis.com/cros-packages/88 buster Release                                          
    Hit:4 https://packages.microsoft.com/repos/vscode stable InRelease                                            
    Hit:5 https://deb.debian.org/debian buster InRelease                           
    Hit:6 https://deb.debian.org/debian-security buster/updates InRelease
    Get:7 https://download.docker.com/linux/debian buster/stable amd64 Packages [17.8 kB]
    Fetched 62.2 kB in 2s (37.7 kB/s)
    Reading package lists... Done
    (ver3.7) connorstom@penguin:~$ sudo apt-get install docker-ce docker-ce-cli containerd.io
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following additional packages will be installed:
    apparmor docker-ce-rootless-extras pigz
    Suggested packages:
    apparmor-profiles-extra apparmor-utils aufs-tools cgroupfs-mount | cgroup-lite
    Recommended packages:
    slirp4netns
    The following NEW packages will be installed:
    apparmor containerd.io docker-ce docker-ce-cli docker-ce-rootless-extras pigz
    0 upgraded, 6 newly installed, 0 to remove and 30 not upgraded.
    Need to get 104 MB of archives.
    After this operation, 453 MB of additional disk space will be used.
    Do you want to continue? [Y/n] y
    Get:1 https://deb.debian.org/debian buster/main amd64 pigz amd64 2.4-1 [57.8 kB]
    Get:2 https://download.docker.com/linux/debian buster/stable amd64 containerd.io amd64 1.4.4-1 [28.3 MB]
    Get:3 https://deb.debian.org/debian buster/main amd64 apparmor amd64 2.13.2-10 [537 kB]
    Get:4 https://download.docker.com/linux/debian buster/stable amd64 docker-ce-cli amd64 5:20.10.5~3-0~debian-buster [41.4 MB]
    Get:5 https://download.docker.com/linux/debian buster/stable amd64 docker-ce amd64 5:20.10.5~3-0~debian-buster [24.8 MB]
    Get:6 https://download.docker.com/linux/debian buster/stable amd64 docker-ce-rootless-extras amd64 5:20.10.5~3-0~debian-buster [8,957 kB]                                                                                                       
    Fetched 104 MB in 40s (2,593 kB/s)                                                                                                                                                                                                              
    debconf: delaying package configuration, since apt-utils is not installed
    Selecting previously unselected package pigz.
    (Reading database ... 46852 files and directories currently installed.)
    Preparing to unpack .../0-pigz_2.4-1_amd64.deb ...
    Unpacking pigz (2.4-1) ...
    Selecting previously unselected package apparmor.
    Preparing to unpack .../1-apparmor_2.13.2-10_amd64.deb ...
    Unpacking apparmor (2.13.2-10) ...
    Selecting previously unselected package containerd.io.
    Preparing to unpack .../2-containerd.io_1.4.4-1_amd64.deb ...
    Unpacking containerd.io (1.4.4-1) ...
    Selecting previously unselected package docker-ce-cli.
    Preparing to unpack .../3-docker-ce-cli_5%3a20.10.5~3-0~debian-buster_amd64.deb ...
    Unpacking docker-ce-cli (5:20.10.5~3-0~debian-buster) ...
    Selecting previously unselected package docker-ce.
    Preparing to unpack .../4-docker-ce_5%3a20.10.5~3-0~debian-buster_amd64.deb ...
    Unpacking docker-ce (5:20.10.5~3-0~debian-buster) ...
    Selecting previously unselected package docker-ce-rootless-extras.
    Preparing to unpack .../5-docker-ce-rootless-extras_5%3a20.10.5~3-0~debian-buster_amd64.deb ...
    Unpacking docker-ce-rootless-extras (5:20.10.5~3-0~debian-buster) ...
    Setting up apparmor (2.13.2-10) ...
    Created symlink /etc/systemd/system/sysinit.target.wants/apparmor.service → /lib/systemd/system/apparmor.service.
    Setting up containerd.io (1.4.4-1) ...
    Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /lib/systemd/system/containerd.service.
    Setting up docker-ce-cli (5:20.10.5~3-0~debian-buster) ...
    Setting up pigz (2.4-1) ...
    Setting up docker-ce (5:20.10.5~3-0~debian-buster) ...
    Created symlink /etc/systemd/system/multi-user.target.wants/docker.service → /lib/systemd/system/docker.service.
    Created symlink /etc/systemd/system/sockets.target.wants/docker.socket → /lib/systemd/system/docker.socket.
    Setting up docker-ce-rootless-extras (5:20.10.5~3-0~debian-buster) ...
    Processing triggers for man-db (2.8.5-2) ...
    Processing triggers for systemd (241-7~deb10u4) ...

    (ver3.7) connorstom@penguin:~$ sudo docker run hello-world
    Unable to find image 'hello-world:latest' locally
    latest: Pulling from library/hello-world
    b8dfde127a29: Pull complete 
    Digest: sha256:308866a43596e83578c7dfa15e27a73011bdd402185a84c5cd7f32a88b501a24
    Status: Downloaded newer image for hello-world:latest

    Hello from Docker!
    This message shows that your installation appears to be working correctly.

    To generate this message, Docker took the following steps:
    1. The Docker client contacted the Docker daemon.
    2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
        (amd64)
    3. The Docker daemon created a new container from that image which runs the
        executable that produces the output you are currently reading.
    4. The Docker daemon streamed that output to the Docker client, which sent it
        to your terminal.

    To try something more ambitious, you can run an Ubuntu container with:
    $ docker run -it ubuntu bash

    Share images, automate workflows, and more with a free Docker ID:
    https://hub.docker.com/

    For more examples and ideas, visit:
    https://docs.docker.com/get-started/

    (ver3.7) connorstom@penguin:~$ docker run -it ubuntu bash
    docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/create: dial unix /var/run/docker.sock: connect: permission denied.
    See 'docker run --help'.

    (ver3.7) connorstom@penguin:~$ 