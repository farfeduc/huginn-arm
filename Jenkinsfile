pipeline {
  agent {
    docker {
      image 'farfeduc/armbuilds'
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