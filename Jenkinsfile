pipeline {
    agent any
    tools {
        terraform 'terraform'
        }
    stages {
//      stage('Git Checkout') {
//             steps {
//                 git 'https://github.com/sansukh/full_vpc'
//             }
//         } 
        stage('Terraform Init') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws creds', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
                {
                sh 'terraform init'
            }
            }
        }
        stage('Terraform Plan') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws creds', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
                {
                sh 'terraform plan'
                }
            }
            }
        stage('Terraform Apply') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws creds', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
                {
                sh 'terraform apply --auto-approve'
                }
            }
        }
        stage('Terraform Destroy') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws creds', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
                {
                
                sh 'terraform destroy --auto-approve'
                }
            }
        }
    }
}

