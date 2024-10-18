pipeline {
    agent any

    stages {
        stage('Test'){
            steps{
                test -f "public/index.html"
            }
        }
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                ls -la
                node --version
                npm --version
                npm ci
                npm run build
                ls -la     
                '''
            }
        }
    }
}
