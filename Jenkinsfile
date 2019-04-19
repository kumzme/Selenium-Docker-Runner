pipeline{
    agent any
    stages{
        stage("Pull Latest Image"){
         steps{
             bat "docker pull learndocker01/selenium-docker"
         }   
        }
        stage("Start Grid"){
         steps{
              bat "docker-compose up -d hub chrome firefox"
         }
        }
        stage("Run Test"){
         steps{
              bat "docker-compose up search-module flight-module"
          }
        }
        // stage("Stop Grid"){
        //     steps{
        //         bat "docker-compose down"
        //     }
        // }
    } 
    post{
        always{
           dir('output') {
           archiveArtifacts artifacts: '**/*',allowEmptyArchive: true
          //archiveArtifacts artifacts: 'search-result'
             bat "docker-compose down"
        }
    }    
    //}  
}
}