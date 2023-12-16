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
        stage('Terraform apply') {
            steps {
                withCredentials([aws(credentialsId: "AWS-Jenkins-Credentials")]) {
                sh 'terraform apply --auto-approve'
                dd_ip = sh(returnStdout: true, script: "terraform output public_ip").trim()
                echo dd_ip
                }
            }
        }
        
    }
}
