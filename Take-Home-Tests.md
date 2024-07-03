
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


![8](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/15eb3244-0d9c-46e3-9640-d88783ca894d)

![9](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/6806acc0-eca9-4422-ac7f-83ab7d1de379)
![10](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/5a3c0268-2e6c-4b9b-8c4a-ac8747f7756e)

![11](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/13642040-6e3e-4743-86af-e7319b4b07d7)

![12](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/c3373672-2cd1-4838-8eae-af2e36c77601)

![13](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/5020ae85-e47f-45cf-bae1-f93364156956)
