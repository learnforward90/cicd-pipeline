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

    stage('docker push') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_creds_id')
          {
            docker.image("abaidalinov/ci-cd-epam:$env.BUILD_NUMBER").push("latest")
          }
        }

      }
    }

  }
}