pipeline {
    agent any
    stages {
        stage('Terraform Init') {
            sh 'cd Terraform'
            sh 'terraform init'
        }
        stage('Terraform Plan') {
            sh 'terraform plan'
        }   
        stage('Terraform Apply') {
            sh 'terraform apply -auto-approve'
        }
 
        stage('Route53') {
            sh 'cd ../Ansible'
            sh 'ansible-playbook S3BucketDeploy.yml'
        }
        stage('CloudFront') {
            sh 'ansible-playbook S3BucketDeploy.yml'
        }
    }
}