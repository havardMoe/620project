# Reinforcement Learning for penetration testing

## Pulling submodules into current repo
(from project folder)
```git submodule update --init --recursive```

## VirtualBox setup
### Network
I created an internal network for VirtualBox and called it `Malfoy`.
This internal network will be used as a seperated network where we do the attacking contain the vulnerable machines used for training and penetration testing.
I then created a dhcp server which assignees IP addresses to machines connected to this network by runnin the context-specific command:
```dhcpserver add --network=Malfoy --server-ip=10.38.1.1 --lower-ip=10.38.1.100 --upper-ip=10.38.1.200 --netmask=255.255.255.0 --enable```

for mac-hosts, you should run this command in the 
```/Applications/VirtualBox.app/Contents``` folder, and
```C:\Program Files\Oracle\VirtualBox``` for windows hosts.

I would reccomend having the vulnerable machines only inside the internal network, but letting the virtual machine running the docker msfconsole docker image be included in both the internal network **and** in a host-only network. This way, you are able to reach the vulnerable machines from the RL-model on the host computer (see figure below) without having them directly connected to your host-network.


### Vulnerable Machines
For initial testing I used the machine `metasploitable-2` from the sourceforge link below and `mrRobot` from vulnhub.
There are different ways of creating vulnerable machines to train a Reinforcement Model on:

#### Metasploitable-2
Is a single unsecure machine using Linux which has a lot of flaws that can be exploited.

Download from ```https://sourceforge.net/projects/metasploitable/```
unzip and start with VirtualBox (debian64)

#### Vulnhub
Is a repository of different vulnerable machines one can download and hack
```https://vulnhub.com/```

#### SecGen
Is a repository which lets you generate virtual machines with random vulnerabilities which can be exploited. Since it lets you generate machines on demand
I do think this will be the best alternative for this project. However, I was unable to get it to run due to version mismatches and syntax-errors in the generated ruby-files.

It will be nice getting this to work in the future as it lets you generate random vulnerable machines in a batch manner, as well as on-demand generation.


### Docker-image containing the metasploit-framework with gRPC communication
```docker pull r0mdau/msf```

Start image with command 

```docker run --rm -i -t -p 9990-9999:9990-9999 -v $HOME/.msf4:/root/.msf4 -v /tmp/msf:/tmp/data --name msf r0mdau/msf```

After starting the dockerfile, start metasploit by running 

```./msfconsole```

and spin up the gRPC service by running

```load msgrpc Pass=[your_pass] ServerPort=[your_port] ServerHost=0.0.0.0 SSL=true```

I downloaded an [Ubuntu image](https://ubuntu.com/download/desktop) and created a virtual machine that ran this docker image, see networking-details above.
