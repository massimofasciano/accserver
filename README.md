# Run ACC Dedicated Server on Linux via Docker

copy the contents of "...\steamapps\common\Assetto Corsa Competizione Dedicated Server"
to a folder on your server such as /root/accserver/app

```
docker run --name accserver --rm --detach \
  -v /root/accserver/app/server:/opt/server \
  -p 9232:9232/tcp \
  -p 9231:9231/udp \
  mafalitic/accserver:latest
```

optionally, place your custom config folder in a separate folder such as
/root/accserver/local/cfg (this keeps it separate from the dist cfg)

you may also create log and results in your local folder to keep them separate

```
docker run --name accserver --rm --detach \
  -v /root/accserver/app/server:/opt/server \
  -v /root/accserver/local/cfg:/opt/server/cfg \
  -v /root/accserver/local/log:/opt/server/log \
  -v /root/accserver/local/results:/opt/server/results \
  -p 9232:9232/tcp \
  -p 9231:9231/udp \
  mafalitic/accserver:latest
```

make sure the 2 ports are allowed by your firewall

the start and stop scripts can be used to automate server control

the start script contains conditional logic that mounts the local cfg, log and results
directories if they exist

