# comment
pipeline {
  stages {
    stage('build') {
      agent { docker { image 'python:3.4-alpine' } }
      steps {
        sh 'python --help'
      }
    }
  }
}
