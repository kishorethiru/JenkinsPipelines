pipeline {
  agent any
  stages {
    stage('Pull Development Code') {
      steps {
        echo 'Dev Code Pulled'
        sleep 5
      }
    }

    stage('Build Dev Code') {
      steps {
        echo 'Stopping Services of running instances'
        echo 'Maven Build the application'
        echo 'Deploy the builded app'
      }
    }

    stage('QA Tests') {
      parallel {
        stage('QA Tests') {
          steps {
            echo 'Starting QA tests'
          }
        }

        stage('Web Tests') {
          steps {
            echo 'Pulling Web Test Code'
            echo 'Executing Web Tests'
          }
        }

        stage('API Tests') {
          steps {
            echo 'Pulling API test code'
            echo 'Executing API Tests'
          }
        }

      }
    }

    stage('QA Certify for UAT') {
      steps {
        input 'Do you want to certify this build?'
      }
    }

    stage('Deploy to UAT') {
      steps {
        echo 'Deployed to UAT'
      }
    }

    stage('QA Certify for Acceptance') {
      steps {
        input 'Do you want to certify this code to prod'
      }
    }

    stage('Prod Deploy') {
      steps {
        echo 'Deploy to prod'
      }
    }

  }
}