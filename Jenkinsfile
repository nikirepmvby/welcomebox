pipeline {
  agent any

  stages {
    stage('Deploy1') {
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
