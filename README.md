# Golang deploy
> This repo is a golang app deploy report

## List of commands
```bash
terraform init
terraform plan
terraform deploy --auto-approve
# Two droplets are created: 
# makuznet-at-gmail-com-server.devops.rebrain.srwx.net
# makuznet-at-gmail-com-client.devops.rebrain.srwx.net

# server
    apt update
    apt -y install git

    # installing Golang 1.13
    wget https://golang.org/dl/go1.13.linux-amd64.tar.gz -P /tmp/
    tar -xzvf /tmp/go1.13.linux-amd64.tar.gz -C /usr/local
    export PATH=$PATH:/usr/local/go/bin
    go version # 1.13
    
    # building the Ethr app
    git clone https://github.com/Microsoft/Ethr
    cd Ethr
        GOOS=linux GOARCH=amd64 go build -o ~/ethr # building the app for linux on PC
        cd ..
    ln -s /root/ethr /usr/local/bin/ethr # adding the app to the system path
    
    # running a server
    ehtr -s # launching a server listening on port 8888 in cli mode
    ethr -s -4 -ui # launching a server listening on port 8888 in pseudo-graphic mode, IPv4 only

# client
    apt update
    apt -y install git

    # installing Golang 1.13
    wget https://golang.org/dl/go1.13.linux-amd64.tar.gz -P /tmp/
    tar -xzvf /tmp/go1.13.linux-amd64.tar.gz -C /usr/local
    export PATH=$PATH:/usr/local/go/bin
    go version # 1.13
    
    # building the Ethr app
    git clone https://github.com/Microsoft/Ethr
    cd Ethr
        GOOS=linux GOARCH=amd64 go build -o ~/ethr # building the app for linux on PC
        cd ..
    ln -s /root/ethr /usr/local/bin/ethr # adding the app to the system path

    # running a client
    ethr -c makuznet-at-gmail-com-server.devops.rebrain.srwx.net
    ethr -c makuznet-at-gmail-com-server.devops.rebrain.srwx.net -p udp -t p -d 0
    ethr -c makuznet-at-gmail-com-server.devops.rebrain.srwx.net -t pi -d 0 -4
    ethr -c makuznet-at-gmail-com-server.devops.rebrain.srwx.net -d 0 -4
```


## Acknowledgments
This repo was inspired by [rebrainme.com](https://rebrainme.com) team

## See also 
- [Github: Microsoft Ethr app](https://github.com/microsoft/ethr)  
- [Golang installation](https://golang.org/doc/install)  
- [Golang downloads](https://golang.org/dl/)  
- [Golang - Building Executables for Different Architectures](https://gist.github.com/zfarbp/121a76d5a3fde562c3955a606a9d6fcc)  


## License
Follow all involved parties licenses terms and conditions.