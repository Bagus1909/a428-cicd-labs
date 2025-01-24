node {
    docker.image('node:16-buster-slim').inside('-u root') {
        stage('Build') {
            sh 'npm install'
        }
        stage('Test') {
            sh './jenkins/scripts/test.sh'
        }
    }
}