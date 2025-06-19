pipeline {
    agent {
        docker {
            image 'node:18'
            args '-u root:root'
        }
    }
    environment {
        APP_NAME = 'node-ci-demo'
        PORT = '3000'
    }
    stages {
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'No build step for this simple app'
            }
        }

        stage('Test') {
            steps {
                echo 'No test step yet'
            }
        }

        stage('Docker Build and Deploy') {
            steps {
                sh '''
                    echo "Building Docker image..."
                    docker build -t $APP_NAME .

                    echo "Stopping previous container..."
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
