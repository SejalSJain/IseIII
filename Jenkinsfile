pipeline
{
environment {
  registry = "maya24/sejalimage"
  registryCredential = 'dockerid'
  dockerImage = ''
}

agent any

stages {
  stage('Build Image') {
    steps {
      script {
        dockerImage = docker.build("${registry}:${BUILD_NUMBER}")
      }
    }
  }

  stage('Deploy the image') {
    steps {
      script {
        withDockerRegistry(credentialsId: registryCredential, url: 'https://index.docker.io/v1/') {
          dockerImage.push()
        }
      }
    }
  }
}
}
