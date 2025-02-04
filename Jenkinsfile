node {
    docker.image('node:16-buster-slim').inside('-u root --network host') {
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
        stage('Deploy') {
            sh './jenkins/scripts/deliver.sh' 
            input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)' 
            sh './jenkins/scripts/kill.sh'
        }
    }
}
