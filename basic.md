# Setup Enviroment

## Install Serverless command line
https://www.serverless.com/framework/docs/getting-started
npm install -g serverless

## AWS CLI
https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
sudo installer -pkg AWSCLIV2.pkg -target /

## OpenAPI Documentation -- Still in the middle of review
Running `generate-open-api.sh` will output the OpenApi yml file (`openapi.yml`) under the root of this directory.
Please refer to https://github.com/conqa/serverless-openapi-documentation to understand how to format/configure the document. 

## Setup AWS credentials
~/.aws/credentials

## Kill the running web server

### Windows
1. Find the app that is using port 8000
netstat -ano | findstr :80
2. Kill by PID (PID is the last column)
tskill PID 

### MAC
1. Find the app that is using port 8000
lsof -i tcp:8000
2. Kill by PID (PID is the last column)
kill -9 PID


## Commands

### Remove Folder (recursive & force)
rm -rf some_dir

## Give permission of the current folder to the current user
whoami
sudo chown -R ${whoami} .
