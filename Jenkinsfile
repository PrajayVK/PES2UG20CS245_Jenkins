pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'g++ main/pes245.cpp -o pes245output'
        build 'PES2UG20CS245-1'
        echo 'Build Successful'
      }
    }
    stage('Test') {
      steps {
        sh './pes245output'
        echo 'Testing Successful'
      }
    }
    stage('Deploy') {
      when {
        expression {
          currentBuild.result == null || currentBuild.result == 'SUCCESS' 
        }
      }
      steps {
        echo 'Deployment Successful'
      }
    }
  }
  post {
    failure {
      echo 'Pipeline failed'
    }
  }
}
