pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                bat 'npm install' 
                bat 'npm run build'
                bat 'dir'
                bat 'cd dist'
                bat 'dir'
            }   
        }
        stage('S3 Upload') {
            steps {
                withAWS(region: 'ap-south-1', credentials: '9de75998-60a2-4e96-9da2-a901e504f62e') {
                    bat 'dir dist'
                    bat 'aws s3 cp build s3://jenkins-node-app/ --recursive'
                }
            }
        }
}
}
