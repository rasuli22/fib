pipeline {
  agent { label 'linux' }
  
  environment {
    DOCKERHUB_CREDENTIALS = credentials('DOCKER_HUB_CRED')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t mrasuli/fibonacci:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push mrasuli/fibonacci:latest'
      }
    }
  }
}
