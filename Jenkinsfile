pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out website code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building website...'
                echo 'No build step required for static HTML website.'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing website...'

                sh '''
                    if [ -f index.html ]; then
                        echo "index.html found successfully."
                    else
                        echo "ERROR: index.html not found!"
                        exit 1
                    fi
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website...'

                sh '''
                    mkdir -p /var/www/html

                    rsync -av --delete \
                    --exclude=".git" \
                    --exclude="Jenkinsfile" \
                    ./ /var/www/html/
                '''

                echo 'Website deployed successfully!'
            }
        }
    }

    post {

        success {
            echo '========================================'
            echo '✅ CI/CD Pipeline completed successfully!'
            echo '✅ Website deployed successfully!'
            echo '========================================'
        }

        failure {
            echo '========================================'
            echo '❌ CI/CD Pipeline failed!'
            echo 'Please check the console output.'
            echo '========================================'
        }

        always {
            echo 'Pipeline execution completed.'
        }
    }
}
