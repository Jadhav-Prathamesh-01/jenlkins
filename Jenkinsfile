pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                git branch: 'main',
                    url: 'https://github.com/Jadhav-Prathamesh-01/jenlkins.git'
                echo 'Source code checked out from Git!'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building the portfolio website...'
                sh 'echo "Build timestamp: $(date)" > build-info.txt'
                echo 'Build completed successfully!'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh '''
                    if [ -f index.html ]; then
                        echo "✓ index.html exists"
                    else
                        echo "✗ index.html not found"
                        exit 1
                    fi
                    
                    if [ -f styles.css ]; then
                        echo "✓ styles.css exists"
                    else
                        echo "✗ styles.css not found"
                        exit 1
                    fi
                '''
                echo 'All tests passed!'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying portfolio website...'
                sh 'echo "Deployment successful at $(date)" >> deployment.log'
                echo 'Portfolio deployed successfully!'
            }
        }
    }
    
    post {
        success {
            echo '✓ Pipeline completed successfully!'
            echo 'Portfolio is ready to be served.'
        }
        failure {
            echo '✗ Pipeline failed. Please check the logs.'
        }
    }
}
