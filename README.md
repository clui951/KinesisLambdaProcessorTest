# kinesis-lambda-processor
Test repo for a Lambda Processor that consumes a Kinesis stream. 
Also included RDS connection capability.

### To Setup Virtual Environment
Create a virtual environment and source it  
```
$ virtualenv -p python3 virtualenv
$ source virtualenv/bin/activate
```
Install requirements
```
$ pip3 install -r lambda/requirements.txt
```

### To Create & Publish Deployment Package
__Note:__ First make sure you have sourced your virtual environment (see above)
```
$ ./publish.sh
```

#### Why is Psycopg2 Dependency Already Included
Psycopg2 is a compiled module, but AWS Lambda does not have the required PostgreSQL libraries in the AMI image to do so. We need to include a version that has been statically pre-compiled on an Amazon Linux machine.
https://github.com/jkehler/awslambda-psycopg2 (use psycopg2-3.6 for python3.6)