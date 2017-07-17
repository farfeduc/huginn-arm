pipeline {
  agent {
    docker {
      image 'armhf/alpine:edge'
    }
    
  }
  stages {
    stage('error') {
      steps {
        sh 'echo \'plop\''
      }
    }
  }
}