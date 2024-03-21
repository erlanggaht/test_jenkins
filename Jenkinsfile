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
       stage('install modules ') {
            steps {
                sh 'npm install '
                echo 'module sedang di install..'
            }
        }
        stage('tes instalt') {
            steps {
                echo 'test function'
            }
        }

        stage('build') {
            steps {
                sh 'npm run build'
                echo 'aplikasi sedang di build..'
            }
        }
        stage('deploy') {
            steps {
                echo 'test berhasil.. proses deploy'
            }
        }
    }

    post {
        failure {
            mail to: 'erlanggahidayat.md@gmail.com', subject: 'Pipeline Failed', body: "${env.BUILD_URL}"
        }
    }
}