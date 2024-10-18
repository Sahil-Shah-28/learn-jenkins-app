pipeline {
    agent any

    stages {
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
        stage('Test'){
            steps{
                echo "In test stage"
                sh '''
                test -f build/index.html 
                npm ci
                node --version
                npm --version
                npm test
                '''
            }
        }
    }
}
