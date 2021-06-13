pipeline {
    agent any

    stages {
        stage('Archive') {
            steps {
                sh '''
                    tar -zcvf files.tar.gz files/
                '''
            }
        }
    
        stage('Upload') {
            steps {
                withAWS(region:'eu-central-1',credentials:'devops-aws-credential') {
                s3Upload(file:'files/', bucket:'devopstask-app-staging');
                }
            }
        }
    }
}