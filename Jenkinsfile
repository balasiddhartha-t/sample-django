
pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    environment {
         DATABASE_URL = 'postgres://postgres:mysecretpassword@192.168.1.60:5432/postgres_db'
      
    }
    stages {
         stage('Clone repository') { 
            steps { 
                script{
                checkout scm
                }
            }
        }

        stage('Build') { 
            steps { 
               sh 'docker build . -t dummyimage:latest'
               //TODO: Need to change the latest to git commit hash
            }
        }
        stage('Push to ACR'){
            steps {
                 echo 'Steps to push into Container Registry'
            }
        }
        stage('Deploy the code into Server'){
            steps{
                  echo 'SSH into server and start the docker container'
                
                  sh 'docker rm -f dummyserver'
                  sh 'docker run --name dummyserver -d -p 8088:8000 dummyimage:latest'
             }
        }

    }
}
