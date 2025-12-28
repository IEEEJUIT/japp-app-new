pipeline {
    agent any

    stages {
        stage('build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true   
                }
            }
            steps {
                sh '''
                   ls -la
                   npm -v
                   npm ci
                   npm run build
                   ls -la
                '''
            }
        }
        stage('test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true   
                }
            }
            steps {
                sh '''
                   npm test
                '''
            }
        }
    }
    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}