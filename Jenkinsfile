pipeline {
    agent any
    tools {
        terraform 'terraform'
    }
    stages {
        stage('Terraform Init') {
            steps {
                dir('Terraform') {
                    sh 'ls'
                    sh 'terraform init'
                }
            }
        }
        stage('Terraform Plan') {
            steps {
                sh 'terraform plan /Terraform'
            }
        }
        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve /Terraform'
            }
        }
        stage('Route53') {
            steps {
                sh 'cd ../Ansible'
                sh 'ansible-playbook S3BucketDeploy.yml'
            }

        }
        // stage('CloudFront') {
        //     steps {
        //         //sh 'ansible-playbook S3BucketDeploy.yml'
        //     }

        // }
    }
}