pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'chmod +x ./scripts/build.sh'
        sh 'script scripts/build.sh'
      }
    }

  }
}