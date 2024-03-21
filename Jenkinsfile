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
        stage("using credential github") {
            steps {
                git branch: "${branch}", credentialsId: "${credentialsId}", url: "${scmUrl}"
            }
        }
       stage('install') {
            steps {
                sh 'npm install '
                echo 'sedang di install..'
            }
        }

        stage('build') {
            steps {
                sh 'npm run build'
                echo 'sedang di build..'
            }
        }
        stage('start') {
            steps {
                sh "npm run start"
                echo 'start ...'
            }
        }
        stage('deploy') {
            steps {
                echo 'build dan start berhasil.. proses deploy'
            }
        }
    }

    post {
        failure {
            mail to: 'erlanggahidayat.md@gmail.com', subject: 'Pipeline Failed', body: "${env.BUILD_URL}"
        }
    }
}