pipeline{
    agent any
    stages{
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