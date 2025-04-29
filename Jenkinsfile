pipeline {
  agent any

  stages{
    stage("cloning code"){
      steps{
        git url:'https://github.com/Metaspolit01/devops-pipeline.git',branch :'main'
      }
    }
   
    stage('build docker image'){
      steps{
        script{
          dockerImage=docker.build("metasploit01/my-image:${BUILD_NUMBER}")
        }
      }
    }

   stage('pushing to dockerhub'){
     steps{
       script{
         docker.withRegistry('https://index.docker.io/v1/','dockerhub-credentials'){
           dockerImage.push()
         }
       }
     }
   }





    
  }
}
