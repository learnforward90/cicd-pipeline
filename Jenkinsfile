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

    stage('docker push') {
      steps {
        sh '''docker.withRegistry(\'https://registry.hub.docker.com\', \'docker_hub_creds_id\')  

{ 
app.push("${env.BUILD_NUMBER}") 
app.push("latest") 
}'''
      }
    }

  }
}