pipeline{
    agent any 
     environment{
                 AWS_DEFAULT_REGION='ap-south-1'
                  S3_BUCKET = 'gokul-frontend'
                }
       stages{
            stage('Checkout'){
                             steps{
                                   git branch: 'gokul',url:'https://github.com/Gokulgejata/gokul-frontend.git'
                                   }
                             }
            stage('Install Dependencies'){
                                         steps{
                                               sh 'npm install'
                                               }
                                           }
            stage('Build'){
                          steps{
                               sh 'npm run build'
                               }
                           }
             stage('Deploy to S3'){
                                  steps{
                                        withCredentials([[$class:'AmazonWebServicesCredentialsBinding',credentialsId: 'aws-credentials']])
                                        {
                                        sh 'aws s3 sync dist s3://gokul-frontend --delete'
                                        }
                                        }
            
               }
         }
