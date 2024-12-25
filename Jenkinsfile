pipeline {
    agent any
     
    parameters { string(name: 'BRANCH', defaultValue: 'main', description: '') }
  
    stages {
      
       stage("github download"){
          
           steps{
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-ssh-auth-cred', url: 'git@github.com:KANTH1069/talent-eks1.git']])
           }
        }
       
       stage("initialize"){
           steps{
               
               sh 'terraform init -migrate-state'
           }
       }
       stage("validation"){
           steps{
               
               sh 'terraform validate'
           }
       }
       stage("planning"){
           steps{
               
               sh 'terraform plan'
           }
       }
       stage("deploy"){
           steps{
               
               sh 'terraform apply --auto-approve'
           }
       }
       
    }
}
       
    
