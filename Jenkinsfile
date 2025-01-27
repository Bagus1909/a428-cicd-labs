node {
    docker.image('node:16-buster-slim').inside('-u root') {
        stage('Checkout') {
            checkout scm
        }
        stage('Build') {
            sh 'npm cache clean --force'
            sh 'rm -rf node_modules package-lock.json'
            sh 'npm install'
        }
        stage('Test') {
            sh './jenkins/scripts/test.sh'
        }
    }
}