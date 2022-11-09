
pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
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
               bat 'docker build . -t dummyimage:latest'
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
                  bat 'docker stop dummyserver'
                  bat 'docker run -d -p 8088:8000 --env-file .env dummyimage:latest'
             }
        }

    }
}
