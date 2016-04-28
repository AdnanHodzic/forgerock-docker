# ForgeRock OpenDJ nightly build

Listens on 389/636/4444

Default bind credentials are CN=Directory Manager, password is 'password'

All writable directories (persisted data) are collected up under /opt/opendj/instances/instance1

To run with Docker (example)
```
mkdir dj    # Make an instance dir to persist data
docker run -i -t -v `pwd`/dj:/opt/opendj/instances/instance1 forgerock/opendj:latest
```

For Kubernetes mount a PV on /opt/opendj/instance/instance1

If you choose not to mount a persistent volume OpenDJ will start OK - but you will lose your data when the container is removed.


# TODO:
Create a strategy for changing the password.  If a secrets volume is present (k8), use that to set the DJ password?


strategy
- instance.loc = /opt/opendj/data
run.sh 
if does not exist 
  run setup 
 if exists and version same 
    start opendj
  if exits and version older
     run upgrade and start 
     
    
  