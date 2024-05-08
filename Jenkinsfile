pipeline {
    agent any
    stages {
        stage("AWS Demo") {
            steps {
                withCredentials([
                    usernamePassword(credentialsId: 'aws_credential', usernameVariable: 'AWS_ACCESS_KEY_ID', passwordVariable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh "aws s3 ls"
                }
            }
        }
        stage("Building AMI") {
            steps {
                withCredentials([
                    usernamePassword(credentialsId: 'aws_credential', usernameVariable: 'AWS_ACCESS_KEY_ID', passwordVariable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh "packer init aws-ami-v1.pkr.hcl"
                    sh "packer build aws-ami-v1.pkr.hcl"
                }
            }
        }
    }
}

