pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'chmod +x ./scripts/build.sh'
        sh 'scripts/build.sh'
      }
    }

  }
}