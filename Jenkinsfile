node {
    docker.image('node:16-buster-slim').inside('-u root') {
        stage('Checkout') {
            checkout scm
        }
        stage('Build') {
            sh 'npm cache clean --force'
            sh 'find node_modules -type d | xargs chmod -R 777'
            sh 'rm -rf node_modules package-lock.json || true'
            sh 'npm install'
        }
        stage('Test') {
            sh './jenkins/scripts/test.sh'
        }
    }
}