pipeline{
  agent any
  stages{
    stage ('checkout'){
      steps{
        checkout scm
      }
    }
   stage ('Build'){
      parallel {
             stage("Angular Build") {
                  agent {
                      docker { image 'node:10' }
                  }
                  steps {
                         sh 'echo installing packages'
                         sh 'npm install'
                         sh 'npm install -g @angular/cli@8'
                         sh 'echo Building Angular Project'
                         sh 'ng build'
                  }
             }
              stage("S3 Build") {
                  steps {
                         //aws cloudformation create-stack --stack-name S3bucketcreation --template-body file:cft.yaml
                         sh 'aws s3api creat-bucket --bucket angular-demo-bucket --region us-east-1'
                  
              }
                
              
       }
   }

    }
}
