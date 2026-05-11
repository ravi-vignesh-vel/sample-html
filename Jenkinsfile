pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/yourrepo/my-static-website.git'
            }
        }

        stage('Deploy to Apache') {
            steps {
                sh '''
                sudo cp -r * /var/www/html/
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'curl localhost'
            }
        }
    }

    post {

        success {
            emailext (
                subject: "SUCCESS: Website Deployment Successful",
                body: "Build Success: ${BUILD_URL}",
                to: "yourmail@gmail.com"
            )
        }

        failure {
            emailext (
                subject: "FAILED: Website Deployment Failed",
                body: "Build Failed: ${BUILD_URL}",
                to: "yourmail@gmail.com"
            )
        }
    }
}