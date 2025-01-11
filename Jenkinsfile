pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'script scripts/build.sh'
      }
    }

    stage('test') {
      steps {
        sh 'script scripts/test.sh'
      }
    }

    stage('docker') {
      steps {
        sh 'docker build -t abaidalinov/ci-cd-epam'
      }
    }

  }
}