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
       stage('build') {
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
        stage('test') {
            steps {
                echo 'test function'
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