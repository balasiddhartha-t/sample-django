
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
             }
        }

    }
}
