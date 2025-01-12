pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/learnforward90/cicd-pipeline', branch: 'main')
      }
    }

    stage('build') {
      steps {
        sh '''chmod +x ./scripts/build.sh
'''
        sh 'scripts/build.sh'
      }
    }

    stage('test') {
      steps {
        sh 'chmod +x ./scripts/test.sh'
        sh 'scripts/test.sh'
      }
    }

    stage('docker build') {
      steps {
        script {
          app = docker.build "${env.DOCKER_IMAGE_TAG}"
        }

      }
    }

    stage('docker push ') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_creds_id')
          {
            app.push("${env.BUILD_NUMBER}")
            app.push('latest')
          }
        }

      }
    }

  }
  environment {
    DOCKER_IMAGE_TAG = 'abaidalinov/ci-cd-epam'
  }
}