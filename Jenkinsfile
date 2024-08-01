pipeline {
    agent any

    stages {
        stage('Setup Virtual Environment') {
            steps {
                echo 'Setting up Python virtual environment...'
                sh 'apt install python3-venv'
                sh 'python3 -m venv myenv'
                sh 'myenv/bin/activate'

            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
                sh '''
                source myenv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                sh '''
                source myenv/bin/activate
                python3 -m unittest discover
                '''
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
                script {
                    input message: 'Approve deployment to production?'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Add deployment commands here for your production environment
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
        always {
            echo 'Cleaning up...'
            // Add cleanup steps if needed
        }
    }
} 
