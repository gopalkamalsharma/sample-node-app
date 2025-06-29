pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('s3-Upload'){
            steps{
                withAWS(region: 'ap-south-1', credentials: '9de75998-60a2-4e96-9da2-a901e504f62e') {
                    sh 'ls -la build'
                    sh 'aws s3 cp build s3://jenkins-node-app/ --recursive'
            }
        }
    }
}
