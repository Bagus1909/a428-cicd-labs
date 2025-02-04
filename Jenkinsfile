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
        stage('Manual Approval'){
            input message: 'Lanjutkan ke tahap Deploy? (Klik "Proceed" untuk mengakhiri)' 
        }
        stage('Deploy') {
            sh './jenkins/scripts/deliver.sh' 
            echo 'aplikasi akan berakhir otomatis setelah 1 menit'
            sleep 60
            sh './jenkins/scripts/kill.sh'
        }
    }
}
