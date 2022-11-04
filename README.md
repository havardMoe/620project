# 620projcet
dat620 project



# Installing metasploitable2
```https://sourceforge.net/projects/metasploitable/```

Unzip and start with VirtualBox



# Pulling docker image for msf - grpc
```docker pull havardmo/dockerfile-msf```

Start image with command 

```docker run --rm -i -t -p 9990-9999:9990-9999 -v $HOME/.msf4:/root/.msf4 -v /tmp/msf:/tmp/data --name msf havardmo/dockerfile-msf```

After starting the dockerfile, start metasploit by running 

```./msfconsole```

and spin up the gRPC service by running

```load msgrpc Pass=[your_pass] ServerPort=[your_port] ServerHost=0.0.0.0 SSL=true```



# Pulling submodules into current repo
(from project folder)
```git submodule update --init --recursive```


