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
        sh 'docker image build -t abaidalinov/epam-ci-cd'
        sh 'docker --version'
      }
    }

  }
}