pipeline {
  agent {
    docker {
      image 'neferius/agent:node-10-docker'
      registryUrl 'https://index.docker.io/v1/'
      registryCredentialsId 'DockerHub-Credentials'
      args '-v /var/run/docker.sock:/var/run/docker.sock'
    }
  }

  stages {
    stage('Deploy') {
      when {
        anyOf {
          branch 'master'
        }
      }
      steps {
        sh "docker ps"
      }
    }
  }
}
