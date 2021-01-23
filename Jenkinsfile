pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './jenkins/build.sh'
        archiveArtifacts(artifacts: 'target/*.jar', fingerprint: true)
      }
    }

    stage('Test') {
      steps {
        sh './jenkins/test-all.sh'
        junit 'target/**/TEST*.xml'
      }
    }

    stage('Deploy') {
      steps {
        sh './jenkins/deploy.sh staging'
      }
    }

  }
}