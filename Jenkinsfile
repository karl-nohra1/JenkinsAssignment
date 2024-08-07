pipeline {
    agent any

    stages {
        stage('Setup Virtual Environment') {
            steps {
                echo 'Setting up Python virtual environment...'
                sh '''
                sudo apt update
                sudo apt install -y python3-venv python3-pip
                python3 -m venv myenv
                sudo chmod -R 755 myenv
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                sh '''
                . myenv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh '''
                . myenv/bin/activate
                python3 -m unittest discover
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add deployment commands here. For example:
                // sh 'scp -r * user@server:/path/to/deploy'
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
 
