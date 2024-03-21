pipeline {
    agent any
    environment {
        branch = 'master'
        scmURL = 'https://github.com/erlanggaht/test_jenkins.git'
        credentialsId = 'erlanggaht' 
    }

    stages {
        stage("checkout git") {
            steps {
                git branch: "${branch}", credentialsId: "${credentialsId}", url: "${scmUrl}"
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