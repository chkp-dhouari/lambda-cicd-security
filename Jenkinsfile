pipeline {
      agent any
     
  stages {
          
         stage('Clone Github repository') {
            
    
           steps {
              
             checkout scm
           
             }
  
          }
    stage('Serverless and CloudGuard Install') {   
       steps {   
                   
         script {      
             try{
                sh 'sudo apt-get update'
                sh 'sudo apt install -y npm nodejs'
                sh 'npm -v'
                sh 'sudo npm install serverless -g'
                sh 'sudo npm install -g https://artifactory.app.protego.io/cloudguard-serverless-plugin.tgz'
                sh 'cloudguard proact -i serverless.yml'
           
                } catch (Exception e){
    
                 echo "Code Analysis is BLOCK and recommend not using the source code"  
                  }
              }
            }
         }
           
           
          stage('Serverless Deploy and CloudGuard SAST/DAST Phase') {
             
            steps {

              sh 'sls deploy'
              
              
             } 
           }
      
        
        
  } 
}
