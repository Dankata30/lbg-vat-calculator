pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    stages {
        stage('Checkout') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', url: 'https://github.com/Dankata30/lbg-vat-calculator.git'
            }
        }

        stage('SCM') {
            steps{
                checkout scm
            }
                
              }

        stage('Build') {
            environment {
                scannerHome= tool 'sonarqube'
            }
            steps {
                // Get some code from a GitHub repository
               withSonarQubeEnv('sonar-qube-1'){
                 sh "${scannerHome}/bin/sonar-scanner"
            }
        }

        }
    }
}
