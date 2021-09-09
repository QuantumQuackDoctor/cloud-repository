pipeline {
    agent any
    tools {
        terraform 'terraform'
    }
    stages {
        stage('Terraform Init') {
            steps {
                sh 'cd Terraform'
                sh 'terraform init'
            }
        }
        stage('Terraform Plan') {
            steps {
                sh 'terraform plan'
            }
        }
        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve'
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