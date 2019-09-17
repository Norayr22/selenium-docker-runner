pipeline{
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
        timeout(time: 5, unit: 'MINUTES')
        ansiColor('xterm')
    }
      stages{
        stage("Pull the latest image"){
            steps{
                bat "docker pull nksanoro/selenium-docker"

            }
        }
        stage("Start Grid"){
            steps{
                bat "docker-compose up -d --scale chrome=2 --scale firefox=2 hub chrome firefox"

            }
        }
        stage("Run Test"){
            steps{
               bat "docker-compose up  search-module1 search-module2 book-flight-module1 book-flight-module2"

            }
        }   
        stage("Generate Report"){
            steps{
            // bat "del output/allure-results"
                allure([
                    includeProperties: false,
                    jdk              : '',
                    properties       : [],
                    reportBuildPolicy: 'ALWAYS',
                    results          : [[path: 'output/allure-results']]
            ])
        }
      }
      }
      post{
            always{
                bat "docker-compose down"
            }
            
    }
}

