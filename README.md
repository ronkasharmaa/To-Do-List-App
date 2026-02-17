# To-Do-List-App (Automated Depolyment Jenkins and Docker containers)
A To Do List App made using nodejs, expressjs, ejs, postgreSQL. Can be auto deployed using Jenkins pipeline

## To run locally without automation and docker:

Prerequisites:
- Install npm
- Install and configure PostgreSQL
- Configure .env file

```sh
cd application
npm i
node app.js
```

## To run with Docker:

Prerequisites:
- Docker

```sh
cd Docker
docker compose up
```

## To run this project with AWS provisioned infra with automation

Prerequisites:
- Jenkins
- Docker
- Ansible
- Terraform
- Jenkins
- AWS CLI

**Set up AWS CLI with you credentials or terraform will not work**

### Setting up Jenkins:
- Create new pipeline
  - Definition: Pipeline script from SCM
  - SCM: Git
  - Repository URL: https://github.com/ronkasharmaa/To-Do-List-App-Automated-Deployment.git
  - Branches to build: */main
  - Script path: Jenkinsfile
- Create Global Credentials

  1)
  - Kind: Secret text
  - Scope: Global
  - Secret: <Your PosgreSQL Password>
  - ID: PGPASSWORD
  - Description: Password for PostgreSQL
  2)
  - Kind: SSH Username with private key
  - Scope: Global
  - ID: ssh key for ec2
  - Description
  - Username: ubuntu/ec2-user (based on what ec2 OS image you use)
  - Private key (Enter Directly): <Your .pem file contents>
  - Passphrase: <empty>
- Run pipeline

**IP Address of ec2 machine will be showed in pipeline logs in the end
Project would be live at http://localhost:3000/ if run locally**
