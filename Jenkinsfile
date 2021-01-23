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
      parallel {
        stage('Test') {
          steps {
            sh './jenkins/test-all.sh'
            junit 'target/**/TEST*.xml'
          }
        }

        stage('Backend') {
          steps {
            sh './jenkins/test-backend.sh'
            junit 'target/surefire-reports/**/TEST*.xml'
          }
        }

        stage('Frontend') {
          steps {
            sh './jenkins/test-frontend.sh'
            junit 'target/test-results/**/TEST*.xml'
          }
        }

        stage('Performance') {
          steps {
            sh './jenkins/test-performance.sh'
          }
        }

        stage('Static ') {
          steps {
            sh './jenkins/test-static.sh'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        sh './jenkins/deploy.sh staging'
      }
    }

  }
}