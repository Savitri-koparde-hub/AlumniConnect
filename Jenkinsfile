pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Savitri-koparde-hub/AlumniConnect.git'
            }
        }

        stage('Check PHP Version') {
            steps {
                sh 'php -v'
            }
        }

        stage('Validate PHP Syntax') {
            steps {
                sh 'find . -name "*.php" -print0 | xargs -0 -n1 php -l'
            }
        }
    }

    post {
        success {
            echo "Build passed 🎉"
        }
        failure {
            echo "Build failed ❌"
        }
    }
}
