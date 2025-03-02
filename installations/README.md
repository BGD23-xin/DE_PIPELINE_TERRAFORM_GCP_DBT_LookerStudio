# Intallations for vm



## 1.connexion to vm


```bash
cd ~/.ssh/
ssh-keygen -t rsa -f (filename) -c (username)

```
copy cat (filename).pub into metadata of gcp


```bash
ssh -i ~/.ssh/(filename) (username)@(external ip)
```

we could also configure a host to connect more easily
```bash
code ~/.ssh/config #use vs code to configure
```

Host name_of_vm
  HostName external_ip
  User username
  IdentityFile ~/.ssh/(filename)

after that, we could connect to VM with `ssh name_of_vm`
## 2.download anaconda

```bash
wget https://repo.anaconda.com/archive/Anaconda3-2021.11-Linux-x86_64.sh

```

## 3.download docker

Perheps, the enviroment could not install docker, it needs to renew the tools:
```bash

sudo apt-get update
sudo apt-get install docker.io

```

check if install correctly

```bash
docker run hello-word
```
after that, if VM could not use docker directly, it needs to watch[guides](https://github.com/sindresorhus/guides/blob/main/docker-without-sudo.md), i run these codes:

```bash
sudo groupadd docker
sudo gpasswd -a $USER docker
sudo service docker restart
```

## 4. download docekr compose

```bash
 mkdir bin &
 cd bin &
 wget https://github.com/docker/compose/releases/download/v2.33.1/docker-compose-linux-x86_64
 &
 mv docker-compose-linux-x86_64 docker-compose
 &
 chmod +x docker-compose
```

add the code `export PATH="${HOME}/bin:${PATH}"` into `.bashrc`.

test if configure correctly:
```bash
which docker-compose
```
## 5.configuration of [docker-compose](https://github.com/BGD23-xin/DE_PIPELINE_TERRAFORM_GCP_DBT_LookerStudio/blob/operations/installations/docker-compose.yaml) file

In this file,we just need to configure 3 apps:
1.Postgres (which is the temporary store of kestra)
2.Kestra (which is the tool of orchestration)
3.pd_admin (which is used to test the codes of kestra are right)

After testing if the code are correct, we could use kestra to download data and load them into bigquery.

```bash
sftp name_of_vm
put file_name
```
this code is used to connect VM and transfer the local files into vm and run them on the VM.

In my side, i use vs code to connect VM. After running code`docker-compose up -d`, we could add ports showing the follow photo:

![photo](https://github.com/BGD23-xin/DE_PIPELINE_TERRAFORM_GCP_DBT_LookerStudio/blob/operations/photos/add_ports.png)

After that, we could open the web in local.

Then we could run the workflow in kestra.

if it does not work because of credentials, you need to add it into environment.
```bash
export GOOGLE_APPLICATION_CREDENTIALS="/home/(USER)/project/keys/(CREDENTIALS FILE)"
```