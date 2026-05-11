pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Deploy HTML to Nginx') {
            steps {
                script {
                    def srcFile = 'index.html'
                    def destDir = '/usr/share/nginx/html'

                    sh "if [ -f ${srcFile} ]; then sudo cp -v ${srcFile} ${destDir}/; else echo '${srcFile} not found' >&2; exit 1; fi"
                }
            }
        }
    }
}
