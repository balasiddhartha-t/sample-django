
pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    environment {
         DATABASE_URL = 'postgres://postgres:mysecretpassword@0.0.0.0:5432/postgres_db'
      
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
                  echo "DATABASE_URL is ${DATABASE_URL}"
                  sh 'docker rm -f dummyserver'
                  sh "docker run --name dummyserver -e DATABASE_URL='postgres://postgres:mysecretpassword@0.0.0.0:5432/postgres_db' -d -p 8888:8000 dummyimage:latest"
             }
        }

    }
}
