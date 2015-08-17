This is an ansible script to setup ruby on rails environment
---

ansible 1.8.2

Vagrant 1.6.3

## vagrant box add 
```
vagrant box add ubuntu15.04 https://github.com/kraksoft/vagrant-box-ubuntu/releases/download/15.04/ubuntu-15.04-amd64.box 
```

## add guest additions
* vagrant up (should raise no guest additions exception)
* vagrant ssh
* add guest additions as below
```
wget http://download.virtualbox.org/virtualbox/4.3.30/VBoxGuestAdditions_4.3.30.iso

sudo mkdir /media/VBoxGuestAdditions

sudo mount -o loop,ro VBoxGuestAdditions_4.3.30.iso /media/VBoxGuestAdditions

sudo sh /media/VBoxGuestAdditions/VBoxLinuxAdditions.run

rm VBoxGuestAdditions_4.3.30.iso

sudo umount /media/VBoxGuestAdditions

sudo rmdir /media/VBoxGuestAdditions
```
## packaging this box
my-virtual-machine should be the name runing in virtual box
```
vagrant package --base my-virtual-machine 
```
the output is **package.box**

## add packaging box
```
vagrant box add vivid_vervet package.box
```
add the **vivid_vervet** as config.vm.box name

## setup env
`vagrant up`

