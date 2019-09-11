pipeline{
    agent any
      stages{
        stage("Start Grid"){
            steps{
                "docker-compose up -d hub chrome firefox"

            }
        }
        stage("Run Test"){
            steps{
                "docker-compose up  search-module1 search-module2 book-flight-module1 book-flight-module2"

            }
        }
        stage("Bring Grid down"){
            steps{
               "docker-compose down"
        }
    }    

    }
}