# Reinforcement Learning for penetration testing


# Vulnerable Hosts
There are different ways of creating vulnerable machines to train a Reinforcement Model on:

## metasploitable 2

Is a single unsecure machine using linux which has a lot of flaws that can be exploited

### Installing metasploitable2
```https://sourceforge.net/projects/metasploitable/```
  Unzip and start with VirtualBox (debian64)

## Vulnhub
Is a repository of different vulnerable machines one can download and hack
```https://vulnhub.com/```

## SecGen
Is a repository which lets you generate virtual machines with random vulnerabilities which can be exploited. Since it lets you generate machines on demand
I do think this will be the best alternative for this project.

The repository is included in this one.


# Pulling docker image for msf - grpc
```docker pull r0mdau/msf```

Start image with command 

```docker run --rm -i -t -p 9990-9999:9990-9999 -v $HOME/.msf4:/root/.msf4 -v /tmp/msf:/tmp/data --name msf r0mdau/msf```

After starting the dockerfile, start metasploit by running 

```./msfconsole```

and spin up the gRPC service by running

```load msgrpc Pass=[your_pass] ServerPort=[your_port] ServerHost=0.0.0.0 SSL=true```



# Pulling submodules into current repo
(from project folder)
```git submodule update --init --recursive```


