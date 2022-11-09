
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
               bat 'docker build ./Dockerfile -t dummyimage:latest'
            }
        }
        stage('Test'){
            steps {
                 echo 'Empty'
            }
        }

    }
}
