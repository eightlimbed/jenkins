pipeline {

  agent none 

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
            sh '''
                echo "Welcome to the first step in the build stage!"
                echo "The date is $(date)"
                echo "Files in $(pwd)"
            '''
            echo "Step complete!"
            echo "USERNAME: ${USERNAME}"
            echo "PASSWORD: ${PASSWORD}"
          }
        }
    }
  }

  post {
    always {
      echo 'POST: Pipeline has finished executing.'
      mail to: 'leetgaines@gmail.com',
           subject: 'Successful Pipeline: ${currentBuild.fullDisplayName}'
           body: 'Check out the pipeline, dawg! Its at ${env.BUILD_URL}'
      deleteDir()
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
