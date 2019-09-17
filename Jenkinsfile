pipeline{
    agent any
      stages{
        stage("Pull the latest image"){
            steps{
                bat "docker pull nksanoro/selenium-docker"

            }
        }
        stage("Start Grid"){
            steps{
                bat "docker-compose up -d hub chrome firefox"

            }
        }
        stage("Run Test"){
            steps{
               bat "docker-compose up  search-module1 search-module2 book-flight-module1 book-flight-module2"

            }
        }   
      }
      post{
            always{
                // bat "del output/allure-results"
                allure([
                    includeProperties: false,
                    jdk              : '',
                    properties       : [],
                    reportBuildPolicy: 'ALWAYS',
                    results          : [[path: 'output/allure-results']]
            ])
        
                bat "docker-compose down"
            }
            
    }
}

