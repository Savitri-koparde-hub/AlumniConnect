pipeline {
    agent any

    environment {
        PATH = "/opt/homebrew/bin:${env.PATH}"
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Check PHP Version') {
            steps {
                sh 'php -v'
            }
        }

        stage('Validate PHP Syntax') {
            steps {
                sh '''
                  echo "Validating PHP syntax..."
                  find . -name "*.php" -print0 | xargs -0 -n1 php -l
                '''
            }
        }

        stage('Build / Test (optional)') {
            steps {
                sh 'echo "Add build or tests here"'
            }
        }
    }

    post {
        always {
            echo "Pipeline completed."
        }
    }
}
