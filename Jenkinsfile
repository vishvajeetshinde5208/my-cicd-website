pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out website code...'
            }
        }

        stage('Build') {
            steps {
                echo 'Building website...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing website...'

                sh '''
                    test -f index.html
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage ready...'
            }
        }
    }

    post {
        success {
            echo '✅ CI/CD Pipeline completed successfully!'
        }

        failure {
            echo '❌ CI/CD Pipeline failed!'
        }
    }
}
