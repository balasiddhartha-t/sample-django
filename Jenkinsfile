pipeline {
  agent {
    node {
      label any
    }
  }

  triggers {
    pollSCM 'H 20 * * 1-5'
  }

  stages {
    stage('checkout') {
      steps {
        checkout scm: [$class: 'GitSCM',
          userRemoteConfigs: [[url: 'git@github.com:balasiddhartha-t/sample-django.git',
                              credentialsId: 'myCredId']],
                              branches: [[name: 'refs/heads/master']]
        ], poll: true
      }
    }
  }
}
 