pipeline {
  agent any

  stages {
    stage('Deploy') {
      when branch 'master'
      steps {
        sh "docker ps"
      }
    }
  }
}
