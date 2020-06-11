pipeline {
     
   agent any
  
   environment{
      INT_FILE = fileExists "master/Interceptors"
      LIB_FILE = fileExists "master/libs"
      APINAME = "master"
      REPO="chaamini/apim-demo"
   }
   
   stages {
      stage('Preparation') {   
         steps{
               git branch: "$APINAME",
               url: "https://github.com/${REPO}.git",
               credentialsId: 'github-chaamini'
         }
      } 
     

      stage('Publishing API to Portal') {
         steps {
            echo "[INFO] - Publishing API to Portal - Begin"
            sh '/usr/bin/python /Users/chaamini/MyWork/Scripts/deploy-api.py tenant'
            echo "[INFO] - Publishing API to Portal - End"
     
         }
      }
   }
   
   post {
      always { 
         cleanWs()
      }
    }
}
