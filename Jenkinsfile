pipeline {
  agent none
  stages {
    stage('build') {
      agent { docker { image 'python:3.4-alpine' } }
      steps {
        sh 'python -c "print(2+5+234)"'
      }
    }
  }
}
