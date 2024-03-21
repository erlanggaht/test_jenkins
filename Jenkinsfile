pipeline {
    agent any
    environment {
        branch = 'master'
        scmURL = 'https://github.com/erlanggaht/test_jenkins.git'
    }

    stages {
        stage('build') {
            steps {
                echo 'sedang di build..'
                sh 'npm run build'
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