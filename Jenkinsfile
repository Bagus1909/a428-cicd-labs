node {
    docker.image('node:16-buster-slim').inside('-u root') {
        stage('Checkout') {
            checkout scm
        }
        stage('Build') {
            sh 'npm cache clean --force'
            sh 'npm config set registry https://registry.npmmirror.com/'
            sh 'npm install --legacy-peer-deps'
        }
        stage('Test') {
            sh './jenkins/scripts/test.sh'
        }
    }
}
