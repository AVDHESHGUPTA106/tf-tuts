pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'GitCredentials', url: 'https://github.com/AVDHESHGUPTA106/tf-tuts'
            }
        }
        stage('Terraform init') {
            steps {
                sh 'terraform init'
            }
        }
        stage('Terraform plan') {
            steps {
                withCredentials([aws(credentialsId: "AWS-Jenkins-Credentials")]) {
                sh 'terraform plan'
                }
            }
        }
        
    }
}
