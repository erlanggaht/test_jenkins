pipeline {
    agent any
    tools {
        nodejs "NODEJS"
    }
    environment {
        branch = 'master'
        scmURL = 'https://github.com/erlanggaht/test_jenkins.git'
        credentialsId = 'erlanggaht' 
    }

    stages {
        stage("Tahap Build") {
            steps {
                git branch: "${branch}", credentialsId: "${credentialsId}", url: "${scmUrl}"
                sh 'npm install '
                echo 'module sedang di install..'
                sh 'npm run build'
            }
        }
        stage('Tahap Test') {
            steps {
                echo 'test function'
            }
        }
        stage('Tahap Deploy') {
            steps {
                echo 'Sedang deploy..'
            }
        }
    }

    post {
        failure {
            mail to: 'erlanggahidayat.md@gmail.com', subject: 'Pipeline Failed', body: "${env.BUILD_URL}"
        }
    }
}