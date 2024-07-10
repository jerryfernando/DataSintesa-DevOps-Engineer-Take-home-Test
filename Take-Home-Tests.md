
# Take-Home Tests

## Overview
Your goal is to set up a simple hello-world Node.js app called oss on a development VM / container.

The code for the simple Express web server as follows :
```
// Simple Express web server
// @see http://howtonode.org/getting-started-with-express

// Load the express module
var express = require('express'); var app = express()


// Respond to requests for / with 'Hello World' app.get('/', function(req, res){
res.send('Hello world!');
});

// Listen on port 80
app.listen(80, () => console.log('Express server started successfully.'));
```

The package.json file as follows :
```
{
"name": "examplenodeapp",
"description": "Example Express Node.js app.",
"author": "dtndevopscandidate <devopscandidate@datasintesa.id>", "dependencies": {
"express": "4.x"
},
"engine": "node >= 0.10.6"
}
```

## Goals
The server should be running :

1.	Centos ≥ 7
2.	Nginx ≥ 1.15
3.	Postgresql ≥ 11 4. Node.js >= 0.10.6

The server must have 3 easily executable bash scripts in /opt/oss/bin :

1.	bin/stop → stop the Express server, nginx, and postgresql.
2.	bin/start → start the Express server, nginx, and postgresql.
3.	bin/backup → dump the postgresql database to a .sqlfile in
/opt/oss/data/backups

## Outputs
A dockerfile or a vagrantfile which fulfills all the goals listed above, along with the 3 executable bash scripts.

Submit the answer to the recruiter max 2 days after day of assignment.

## Answer
centos7
![1](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/8f139122-ec81-4278-9cf0-a6dfe60fb4ff)

File repositori YUM untuk CentOS biasanya berada di direktori /etc/yum.repos.d/. File yang perlu Anda edit adalah CentOS-Base.repo. hapus semua dan copas yg dibawah ini

````
[base]
name=CentOS-$releasever - Base
baseurl=http://mirror.centos.org/centos/$releasever/os/$basearch/
        http://mirror.centos.org/centos/$releasever/os/$basearch/
        http://vault.centos.org/centos/$releasever/os/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7

[updates]
name=CentOS-$releasever - Updates
baseurl=http://mirror.centos.org/centos/$releasever/updates/$basearch/
        http://mirror.centos.org/centos/$releasever/updates/$basearch/
        http://vault.centos.org/centos/$releasever/updates/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7

[extras]
name=CentOS-$releasever - Extras
baseurl=http://mirror.centos.org/centos/$releasever/extras/$basearch/
        http://mirror.centos.org/centos/$releasever/extras/$basearch/
        http://vault.centos.org/centos/$releasever/extras/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7

[centosplus]
name=CentOS-$releasever - Plus
baseurl=http://mirror.centos.org/centos/$releasever/centosplus/$basearch/
        http://mirror.centos.org/centos/$releasever/centosplus/$basearch/
        http://vault.centos.org/centos/$releasever/centosplus/$basearch/
gpgcheck=1
enabled=0
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7

````
```
sudo yum clean all

```

```
sudo yum update

```

Daftar Mirror Alternatif
Berikut adalah beberapa mirror alternatif yang bisa Anda gunakan. Anda bisa menambahkan atau mengganti baseurl di file CentOS-Base.repo dengan salah satu URL berikut:

Mirror from CentOS
http://mirror.centos.org/centos/
http://vault.centos.org/centos/

Mirror from Kernel.org
http://mirrors.kernel.org/centos/

Mirror from Duke University
http://mirror.lug.udel.edu/pub/centos/

Mirror from Fastly
http://mirror.fastly.net/centos/

Mirror from EPEL
https://dl.fedoraproject.org/pub/epel/



install docker  
```
#!/bin/bash

# Perbarui paket yang ada di sistem
sudo yum update -y

# Instal beberapa paket yang diperlukan sebelum menginstal Docker
sudo yum install -y yum-utils device-mapper-persistent-data lvm2

# Tambahkan repository Docker ke sistem
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

# Instal Docker menggunakan perintah berikut
sudo yum install -y docker-ce docker-ce-cli containerd.io

# Mulai layanan Docker dan aktifkan agar otomatis berjalan saat sistem dinyalakan

sudo systemctl start docker
sudo systemctl enable docker
```

![2](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/80960607-6bb1-400c-9b04-1cad8d2b9deb)

# create app

create index.js
```
sudo nano index.js
```
```
// Simple Express web server
// @see http://howtonode.org/getting-started-with-express
// Load the express module
var express = require('express');
var app = express();

// Respond to requests for / with 'Hello World'
app.get('/', function(req, res){
  res.send('Hello world!');
});

// Listen on port 80
app.listen(80, () => console.log('Express server started successfully.'));
```
create package.json
```
sudo nano package.json
```
```
{
  "name": "examplenodeapp",
  "description": "Example Express Node.js app.",
  "author": "dtndevopscandidate <devopscandidate@datasintesa.id>",
  "dependencies": {
    "express": "4.x"
  },
  "engine": "node >= 0.10.6"
}
```
```
mkdir bin
```
create bin/start
```
sudo nano start
```
```
#!/bin/bash

# Start the Express server, nginx, and postgresql

/usr/libexec/docker/cli-plugins/docker-compose up -d
```
![4](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/aeb0825e-8021-4e7a-a4d1-5055f0bf2ef0)

create bin/stop
```
sudo nano stop
```
```
#!/bin/bash

# Stop the Express server, nginx, and postgresql

/usr/libexec/docker/cli-plugins/docker-compose down
```
![5](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/494026cb-9e0b-4a9a-9747-ee04a7f81826)

create backup
```
sudo nano backup
```
```
TIMESTAMP=$(date +"%F")
BACKUP_DIR="/opt/oss/data/backups"
BACKUP_FILE="$BACKUP_DIR/backup_$TIMESTAMP.sql"

docker exec -t $(/usr/libexec/docker/cli-plugins/docker-compose ps -q db) pg_dumpall -c -U user > $BACKUP_FILE

echo "Backup saved to $BACKUP_FILE"
```
![6](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/e192995e-177a-480d-9637-3c70580101cc)

```
sudo chmod +x /bin/stop /bin/start /bin backup
```
![3](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/15110854-57d9-4b9f-99d8-07014608e55d)

create nginx.conf
```
sudo nano nginx.conf
```
```
events {
  worker_connections 1024;
}

http {
  server {
    listen 80;
    server_name app.studentdumbways.my.id;

    location / {
      proxy_pass http://103.127.97.172:80;
      proxy_set_header Host $host;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Proto $scheme;
    }
  }
}
```

create Dockerfile
```
sudo nano Dockerfile
```
```
FROM node:20.14.0-alpine

# Create and change to the app directory
WORKDIR /usr/src/app

# Copy package.json and install dependencies
COPY package.json ./
RUN npm install

# Copy the app source code
COPY . .

# Expose the port the app runs on
EXPOSE 80

# Run the app
CMD ["node", "index.js"]
```

create docker-compose

```
sudo nano docker-compose.yml

```
```
services:

  db:
    image: postgres:13
    environment:
      POSTGRES_DB: mydb
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
    volumes:
      - db_data:/var/lib/postgresql/data
    networks:
      - oss-net

  web:
    build: .
    ports:
      - "80:80"
    depends_on:
      - db
    networks:
      - oss-net

  nginx:
    image: nginx:latest
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
    ports:
      - "8080:80"
    depends_on:
      - web
    networks:
      - oss-net


networks:
  oss-net:

volumes:
  db_data:
```

![7](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/e76103bc-3652-4260-bc27-a1d5a53d5dec)
