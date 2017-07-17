pipeline {
  agent {
    docker {
      image 'docker-agent'
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