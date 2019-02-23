pipeline {
  agent any

  stages {
    stage('Check') {
      when {
        branch 'master'
      }
      steps {
        sh "docker ps"
        sh "ls"
        sh "pwd"
      }
    }
    stage('Deploy') {
      when {
        branch 'master'
      }
      environment {
        repo = "neferius/welcomebox"
        branch_lower = "${BRANCH_NAME.toLowerCase()}"
        timestamp = VersionNumber(versionNumberString: '${BUILD_DATE_FORMATTED, "yyyy-MM-dd HH:mm:ss"}')
      }
      steps {
        sh """
          docker build \
            -f docker/Dockerfile \
            --build-arg "BUILD_TIME=${timestamp}" \
            --build-arg "GIT_COMMIT=${GIT_COMMIT}" \
            --label lastingdynamics.project=welcomebox \
            --label lastingdynamics.branch=${branch_lower} \
            --label lastingdynamics.commit=${GIT_COMMIT} \
            -t ${repo}:${branch_lower} \
            .
        """
        sh "docker push ${repo}"
      }
    }
  }
}
