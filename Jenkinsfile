pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'chmod +x ./scripts/build.sh'
        sh 'scripts/build.sh'
      }
    }

    stage('test') {
      steps {
        sh 'scripts/test.sh'
      }
    }

    stage('docker build') {
      steps {
        sh 'docker build -t abaidalinov/ci-cd-epam .'
      }
    }

  }
}