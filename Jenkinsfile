pipeline {
  agent any
  stages {
    stage('Fluffy Build') {
      steps {
        echo 'Build Step'
      }
    }

    stage('Fluffy Test') {
      steps {
        sh '''echo Slepping for 5 secs...
sleep 5
echo I wokeup'''
      }
    }

    stage('Fluffy Deploy') {
      steps {
        echo 'Final Deployment'
        sh 'echo Deployment is done.'
      }
    }

  }
}