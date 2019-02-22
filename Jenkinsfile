pipeline {
  agent any

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
