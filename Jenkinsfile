pipeline {

  # "agent any" -- what if you have no agent? 
  agent none 

  # environment variables -- in what context?
  environment {
    USERNAME = 'theodore'
    PASSWORD = 'password123'
  }

  stages {

    stage('jenkins_test') {
      agent any
      steps {
        sh 'printenv'
        sh 'whoami'
      }
    }

    stage('build') {
      agent { docker { image 'python:3.4-alpine' } }
      steps {
        timeout(time: 1, unit: "MINUTES") {
          retry(3) {
            sh '''
                echo "Welcome to the first step in the build stage!"
                echo "The date is $(date)"
                echo "Files in $(pwd)"
                ls
            '''
            sh 'cmatrix'
            echo "Step complete!"
          }
        }
      }

    }
  }

  post {
    always {
      echo 'POST: Pipeline has finished executing.'
    }
    success {
      echo 'POST: Pipeline was a success.'
    }
    failure {
      echo 'POST: Pipeline failed.'
    }
    unstable {
      echo 'POST: Unstable pipeline.'
    }
    changed {
      echo 'POST: The state of the Pipeline has changed.'
    }
  }

}
