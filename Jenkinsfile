pipeline {
    agent {
        docker {
            image 'node:18'
        }
    }
    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/DhavalBhimani44/jenkins-ci-cd-pipeline'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                echo 'No build step for simple Node app!'
            }
        }
        stage('Test') {
            steps {
                echo 'No tests defined yet!'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh 'docker build -t node-ci-demo .'
                sh 'docker run -d -p 3000:3000 --name ci-demo-app node-ci-demo'
            }
        }
    }
}
