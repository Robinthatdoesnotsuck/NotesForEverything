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

+ Provisioning refers to a way to make the VM to access resources on the host machine
+ So to do this we will enable the httpd services on our virtual box
+ We sill add a section on scripting with httpd
    + We will use a section to enable this httpd variable on the Vagrantfile 
    ```
    $httpd = <<SCRIPT
    yum install httpd
    systemctl start httpd
    systemctl enable httpd
    SCRIPT
    ```
+ Then we will add to our Vagrantfile this
    ```
    config.vm.provision "shell", inline: $httpd
    ```
    + This provision method will let us declare the channel that we will use to provision 
    + This shell will provisioning tells us that is going to provide by an inline command on the shell, we can also use a path to a bash script if instead of ```ìnline: whatever``` we used instead ```path: "pathtoscript"```

+ Also we can share files between vm and host if we synced the files that why we can add
```config.vm.synced_folder ".", "/home/vagrant/stuff"``` this will sync the files that are living inside your current directry(hence the .) and the path on the vm(the thing after the coma) 
+ After this we need to make sure that the VM is down or halted or or we can also use the vagrant command
    ```
    vagrant provision <vm-name>
    ```
+ But it's better to halt the VM and use the ```--provision``` flag when we run the vm up the ```vagrant up```

## Multi machine management with multiple vagrant files

+ Since it is logical the good thing in vagrant it is that we can define multiple vms for different purposes, like one for dbs other as a webserver, other one as a loadbalancer, etc.
+ So it is naturally that vagrant lets us manage them easily in our vagrant file, or multiple ones
+ To do this we can add to our vagrant file nodes that we will use as our different purpose vms
    ```
    config.vm.define "nodex" do |nodex|
        nodex.vm.box = "distro"
        nodex.vm.hostname = "purpose"
    end
    ```
    + And we can add this to the x number of nodes and x number of properties that we want to add
    + We can also add a primary machine, this machine will be the one that you will ssh incase that you don't specify which machine to ssh using ``` vagrant ssh [vm-name or host-name]```

## Commands

+ Common commands
    ```
    vagrant init [name [url]] ## This creates the vagrant file and depending on the flags it is going to contain something different, while doing this you make the current directory into a vagrant environment
    vagrant up [name|id]
    vagrant status [name|id]
    vagrant halt [name|id] ## Stops the vm and conserves the configuration you can add the flag -f to just halt it without confirmation
    vagrant destroy [name|id] ## Straight up kills the machine
    vagrant ssh [name|id] ## This makes you login to the specific vm that you want via ssh
    vagrant suspend [name|id]
    vagrant resume [name|id]
    vagrant box add ADDRESS ## This just adds the image to the host so that vagrant can access it
    vagrant global-status
    vagrant reload ## Just reloads the machine
    vagrant login ## Makes you login with the Hashicorp vault so it is not a requirement
    vagrant ssh-config ## This only gives you a valid configuration for SSH into the running vagrant machine
    vagrant provision ## If we add data provision this command makes that change on the running environment
    vagrant port ## Shows the list of guest ports mapped to the host ports in use
    vagrant status ## Shows you the status of the current vagrant environment (this means you have to be in a directory with a a VagrantFile)
    vagrant global-status ## Shows you the state of all vms
    ```

+ Commands on vagrant file
    ```
    config.vm.post_up_message[...] ## This will output instructions on various components after running vagrant up
    ```
