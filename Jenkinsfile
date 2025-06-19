pipeline {
    agent none

    environment {
        APP_NAME = 'node-ci-demo'
        PORT = '3000'
    }

    stages {
        stage('Install Dependencies') {
            agent {
                docker {
                    image 'node:18'
                    args '-u root:root'
                }
            }
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            agent {
                docker {
                    image 'node:18'
                    args '-u root:root'
                }
            }
            steps {
                echo 'No build step for this simple app'
            }
        }

        stage('Test') {
            agent {
                docker {
                    image 'node:18'
                    args '-u root:root'
                }
            }
            steps {
                echo 'No test step yet'
            }
        }

        stage('Docker Build and Deploy') {
            agent { label 'docker-host' } // your Jenkins host/container with Docker CLI
            steps {
                sh '''
                    echo "Building Docker image..."
                    docker build -t $APP_NAME .

                    echo "Stopping previous container if exists..."
                    docker rm -f $APP_NAME || true

                    echo "Running new container..."
                    docker run -d -p $PORT:$PORT --name $APP_NAME $APP_NAME
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
    }
}
