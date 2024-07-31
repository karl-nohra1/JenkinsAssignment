pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'python3 -m unittest discover'
            }
        }

        stage('Deploy to Test Environment') {
            steps {
                echo 'Deploying to Test Environment...'
                // Add deployment commands here for your test environment
            }
        }

        stage('Approval') {
            steps {
                input 'Approve deployment to production?'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Add deployment commands here for your production environment
            }
        }
    }
}
