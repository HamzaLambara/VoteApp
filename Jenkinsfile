pipeline{
    agent any
    stages {
        stage('Clone the project'){
            steps{
                git branch: 'main', url: 'https://github.com/HamzaLambara/VoteApp.git'
            }
        }
        stage('Build'){
            steps {
                dir("BackendofADEIVotechain"){
                    sh "chmod 777 ./mvnw"
                    sh "./mvnw clean install -DskipTests"
                }
                
            }
        }
        /*stage('Test'){
            steps{
                dir('BackendofADEIVotechain'){
                    sh "./mvnw test"
                }
            }
        }*/
        stage('Deploy-Backend'){
            steps{
                dir('BackendofADEIVotechain'){
                    sh "docker build -t my-backend-2 ."
                    sh "docker login -u hamzalambara -p plazma235"
                    sh "docker pull hadryyassine/adeivotechain-1:my-backend-2"
                    sh "docker push hadryyassine/adeivotechain-1:my-backend-2"
                }
            }
            
        }
    }
}
