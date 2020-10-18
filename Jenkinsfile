pipeline {
  environment {
    registry = "satya1208/testing-123"
    registryCredentials = "DockerHub"
    dockerImage = ''
  }
  agent any
  stages {
    stage('Build Docker Image') {
      steps {
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
        }
      }
    
    stage ('Push to DockerHub') {
      steps {
        script {
        docker.withRegistry('', registryCredentials ) {
          docker.Image.push()
        }
      }
      }
    }
      
    stage('Test Run') {
        steps {
          sh 'docker run -d $registry:$BUILD_NUMBER'
        }
  }
    }
  }
