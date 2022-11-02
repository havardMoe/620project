# 620projcet
dat620 project



# Installing metasploitable2
```https://sourceforge.net/projects/metasploitable/```


# Pulling docker image for msf - grpc
```docker pull havardmo/dockerfile-msf```
Run with command ```docker run --rm -i -t -p 9990-9999:9990-9999 -v $HOME/.msf4:/root/.msf4 -v /tmp/msf:/tmp/data --name msf havardmo/dockerfile-msf```

# Pulling submodules into current repo
(from project folder)
```git submodule update --init --recursive```


