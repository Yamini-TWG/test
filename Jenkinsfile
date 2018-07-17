



   pipeline {
  agent {
    node {
      label 'jdk8'
    }

  }
  stages {
    stage('Hello') {
      steps {
        echo "Hello ${params.Name}!"
        sh 'java -version'
        echo "${TEST_USER_USR}"
        echo "${TEST_USER_PSW}"
      }
    }
  }
}
