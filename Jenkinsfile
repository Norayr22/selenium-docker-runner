pipeline{
    agent any
    stages{
        stage("Run Test"){
            steps{
                "docker-compose up"
            }
        }
        stage("Bring Grid down"){
            steps{
               "docker-compose down"
        }
    }    

    }
}