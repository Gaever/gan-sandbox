# GPU hosting

https://immers.cloud

# Access
`GPU_CLOUD_IP` could be found under https://immers.cloud/vm/ 
```sh
export GPU_CLOUD_IP=<vm_ip_addr>

ssh -i ~/.ssh/immers-cloud.pem -p22 ubuntu@${GPU_CLOUD_IP}
```

# Install enviroment
```sh
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
# sudo apt install python3.8

sudo apt-get -y install python3.8 python-setuptools python3-setuptools python-pip python3-pip
pip install wheel torchvision tensorboardx jupyter matplotlib numpy

mkdir ~/gan
```

# Run
Proxy jupiter notebook to local machine's `localhost:8888`.

```sh
ssh -L 8888:localhost:8888 ubuntu@${GPU_CLOUD_IP}
jupiter notebook
```

Allocate `token` in console output and paste it in browser as prompt.
```
[C 04:18:15.855 NotebookApp] 
    
    To access the notebook, open this file in a browser:
        file:///home/ubuntu/.local/share/jupyter/runtime/nbserver-3238-open.html
    Or copy and paste one of these URLs:
        http://localhost:8888/?token=<token>
     or http://127.0.0.1:8888/?token=<token>
```


# Upload
```sh
export GPU_CLOUD_IP=<vm_ip_addr>
./deploy.sh
```
Script will copy `./src` to VM's catalog.
