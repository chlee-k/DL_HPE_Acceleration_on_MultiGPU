# DL HPE Acceleration on MultiGPU #
we use docker container which is a kind of virtualization because of 5G MEC environment.
## Prerequisite ##
docker, nvidia-docker, python, aioRTC, pytorch, etc.

## Docker Run Commandline (mandatory arguments) ##
```docker run --gpus all -it --net host --ipc=host dlckdgk/kaist:vrar-LATEST /bin/bash```

## Make openssl self signed certificate ##
### server-side ###
create a server private key:
```
openssl genrsa -des3 -out server.key 2048
(enter your password)
```

generate a server csr:
```
openssl req -new -key server.key -out server.csr
(enter information and common domain which is necessary)
```

remove password in server private key:
```
cp server.key server.key.origin
openssl rsa -in server.key.origin -out server.key
(enter your assigned password)
```

create a self-signed server crt:
```
openssl x509 -req -days 3650 -in server.csr -signkey server.key -out server.crt
```

## Run aioRTC server application ##
```
python server.py --cert-file ./server.crt --key-file ./server.key --host {IP.ADDRESS}
```
