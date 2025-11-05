## install dep 

```sh 
npm install 
```
## start server 
PORT=3000 npm start

## run postgers server

```sh 
docker compose up 
```


## install postgeres-client
```sh 
sudo apt-get install postgresql-client
```
## create database 
createdb study-sync   -h localhost  -U admin 
## connect to database 
```sh
psql postgresql://admin:admin123@localhost:5432/study-sync
```


## Create Schema
```sh
psql study-sync < db/sql/schema.sql -h localhost -U postgres
```
## Import Data
```sh
psql study-sync < db/sql/seed.sql -h localhost -U postgres
```

## Verify Data

```sh
psql postgresql://admin:admin123@localhost:5432/study-sync
```

```sql
SELECT * FROM questions;
```


# Install EB CLI
```sh
# 1️⃣ Update packages
sudo apt update

# 2️⃣ Install virtualenv from apt (recommended on Ubuntu 24.04)
sudo apt install -y python3-virtualenv

# 3️⃣ Verify it's installed
virtualenv --version
virtualenv -p python3 ~/ebcli-venv

```
## active it 
```sh
source ~/ebcli-venv/bin/activate

```
##  Install the Elastic Beanstalk CLI
```sh 
pip install --upgrade pip
pip install awsebcli --upgrade

```


## Manual Install if you don't have to do the virtual enviroment (optional)
```sh
git clone https://github.com/aws/aws-elastic-beanstalk-cli-setup.git
sudo apt install python-is-python3
python3 ./aws-elastic-beanstalk-cli-setup/scripts/ebcli_installer.py
echo 'export PATH="/home/gitpod/.ebcli-virtual-env/executables:$PATH"' >> ~/.bash_profile && source ~/.bash_profile
```
## Initialize EB
```sh
eb init
```

## Set Codesource
```sh
eb codesource
```
## Zip Directory
```sh
zip -r app.zip app
```

## Unzip Directory
```sh
 unzip app.zip 
```

## Make Config Var for Eb Extensions
```sh 
mkdir .ebextensions touch .ebextensions/001_envar.config
```
## Create IAM Profile
```sh
aws iam create-instance-profile --instance-profile-name StudySyncInstanceProfile
aws iam add-role-to-instance-profile \
    --role-name AWSElasticBeanstalkWebTierRole  \
    --instance-profile-name StudySyncInstanceProfile
```
## Importing into RDS
```sh 
psql study-sync < sql/schema.sql -h rds-basic-rdsinstance-uzdzjcuz1opq.cv1x0r3utzcm.ca-central-1.rds.amazonaws.com -U postgres psql study-sync < sql/seed.sql -h rds-basic-rdsinstance-uzdzjcuz1opq.cv1x0r3utzcm.ca-central-1.rds.amazonaws.com -U postgres
```