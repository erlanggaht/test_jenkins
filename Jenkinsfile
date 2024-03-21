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
                git branch: "${branch}", credentialsId: "${82aa2d26-ef4b-4a6a-a05f-2e1090b9ce17}", url: "${scmUrl}"
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