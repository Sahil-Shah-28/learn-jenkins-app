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
       stage('Test') {
    steps {
        echo "In test stage"
        script {
            // Check if the file exists
            def fileExists = sh(script: 'test -f "build/index.html"', returnStatus: true)
            if (fileExists == 0) {
                echo 'build/index.html exists.'
            } else {
                error 'build/index.html does not exist. Build might have failed.'
            }
        }
    }
}

    }
}
