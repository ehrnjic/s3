pipeline {
    agent any

    stages {
        stage('Archive') {
            steps {
                sh '''
                    //tar -zcvf files-${BRANCH}-${BUILD_NUMBER}.tar.gz files/
                    tar -zcvf files.tar.gz files/
                '''
            }
        }
    }

    stage('Upload') {
        steps {
            withAWS(region:'eu-central-1',credentials:'devops-aws-credential') {
            //def identity=awsIdentity();
            //s3Upload(file:'files.tar.gz', bucket:'devopstask-app-staging');
            s3Upload(file:'files.tar.gz', bucket:'devopstask-app-staging', path:'tarfiles/');
            }
        }
    }
}