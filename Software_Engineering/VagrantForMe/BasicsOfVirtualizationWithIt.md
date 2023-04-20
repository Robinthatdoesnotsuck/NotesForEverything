# Vagrant is a usefool tool for idk

## The fundamentals
+ Vagrant is a virtualization tool that helps us automate all sorts of stuff regarding well virtualization
+ To do this we just need a vagrantfile in a directory that we are going to use as a working directory
    + If you don't have a base image you can just pull it from the vagrant cloud and run it like this
        ```
        vagrant init ubuntu/xenial64
        ```
    + This will create the initial vagrantfile that we are going to use to run our virtualization environment

+ Then we only have to use ```vagrant up ``` to start the ubuntu/xenial64 virtualization
+ And to access it once it is downloaded and up we just need to run ```vagrant ssh```

## Vagrantfile

+ This file is the soul of the VM, since it is a declarative way of describing our vm on the Ruby Language

+ So a way to get started its to add a box of any distro in your vagrant
    ```vagrant box add centos/7```
    + This will add the additional image that we are going to use in this case centos 7
    + Then we will use ```vagrant init --minimal``` to create a minimal vagrant file that we'll modify
    + This file will have this
    ```
    Vagrant.configure("2") do |config|
      config.vm.box = "base"
    end
    ```
    + This file needs to be modified to be able to work with the image that we added in the box
    ```
    Vagrant.configure("2") do |config|
        config.vm.box = "centos/7"
        config.vm.provider "virtualbox" do |vb|
            vb.memory = "1024"
            vb.cpus = "2"
        end
    end
    ```
+ This file tells us to run the Vagrant configuration version 2 and that the image that we will be using is centos/7
+ Also tells us that the provider that we are goint to use is VirtualBox, so we do that in that command of ```config.vm.provider "virtualbox"```
+ Then we can add a hostname to that vm with ```config.vm.hostname = "server.example.com"```

## Networking with vagrant

+ For practicing purposes we will use the private ip addresses ranges

| From            | To               | 
|-----------------|:----------------:|
| 10.0.0.0        |  10.255.255.255  |
| 172.16.0.0      |  172.31.255.255  |
| 192.168.0.0     |  192.168.255.255 |

+ And depending on it the classes of them
| Class | 	From 	| To | 
|A| 	0.0.0.0 	| 127.255.255.255 |
|B| 	128.0.0.0 	| 191.255.255.255 |
|C| 	192.0.0.0 	| 223.255.255.255 |
|D| 	224.0.0.0 	| 239.255.255.255 |
|E| 	240.0.0.0 	| 255.255.255.255 |

+ Class A, B, and C are public IP that are unicast, this means that only a single device can try to connect to another one on the internet
+ Class D are multicast addresses this means on the contrary a single device can connect to multiple devices
+ Class E are reserved for experimental purposes only

+ So knowing this we can add network settings to our vagrantfile
    + With ```config.vm.network "private_network, ip: [Private_ip]```
+ And to make it accessible to anyone with a public network we just have to use
    + The command on ruby with ```config.vm.network "public_network"```

## Provisioning and Data sharing on Vagrant

## Commands

+ Common commands
    ```
    vagrant init [name [url]]
    vagrant up [name|id]
    vagrant status [name|id]
    vagrant halt [name|id]
    vagrant destroy [name|id]
    vagrant ssh [name|id]
    vagrant suspend [name|id]
    vagrant resume [name|id]
    vagrant box add ADDRESS
    vagrant global-status
    ```
