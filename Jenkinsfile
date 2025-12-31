pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Savitri-koparde-hub/AlumniConnect.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    bat '''
                    "C:\\sonar-scanner-8.0.1.6346-windows-x64\\bin\\sonar-scanner.bat" ^
                      -Dsonar.projectKey=AlumniConnect ^
                      -Dsonar.sources=. ^
                      -Dsonar.language=php ^
                      -Dsonar.host.url=http://localhost:9000 ^
                      -Dsonar.login=%SONAR_AUTH_TOKEN%
                    '''
                }
            }
        }

        stage('Check PHP Version') {
            steps {
                bat 'php -v'
            }
        }

        stage('Validate PHP Syntax') {
            steps {
                bat 'for /R %%f in (*.php) do php -l "%%f"'
            }
        }
    }
}
