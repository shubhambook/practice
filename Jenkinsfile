pipeline {
    agent any

    environment {
        DEPLOY_DIR = "/var/www/html"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'jenkins1',
                    url: 'https://github.com/shubhambook/practice.git'
            }
        }

        stage('Validate Code') {
            steps {
                sh '''
                echo "Listing workspace files"
                ls -la
                '''
            }
        }

        stage('Build') {
            steps {
                echo 'Static website – no build required'
            }
        }

        stage('Deploy to Nginx') {
            steps {
                sh '''
                echo "Deploying website to Nginx"
                sudo rm -rf ${DEPLOY_DIR:?}/*
                sudo cp -r ./* ${DEPLOY_DIR}/
                sudo chown -R www-data:www-data ${DEPLOY_DIR}
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Website deployed successfully'
        }
        failure {
            echo '❌ Deployment failed'
        }
    }
}
