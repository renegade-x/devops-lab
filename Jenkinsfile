 	pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Fetching source code from GitHub'
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Running build checks'
                sh 'bash test.sh'
            }
        }
        stage('Test') {
            steps {
                echo 'Checking the page content'
                sh 'grep -q "Student:" index.html'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Publishing to Nginx'
                sh 'cp index.html /usr/share/nginx/html/index.html'
            }
        }
    }

    post {
        success { echo 'Pipeline finished successfully' }
        failure { echo 'Pipeline failed: nothing was deployed' }
    }
}
