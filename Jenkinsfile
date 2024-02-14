pipeline {
    agent any
    stages {
        stage('Clone the project') {
            steps {
                git branch: 'main', url: 'https://github.com/HamzaLambara/VoteApp.git'
            }
        }
        stage('Build') {
            steps {
                dir("BackendofADEIVotechain") {
                    sh "chmod 777 ./mvnw"
                    sh "./mvnw clean install -DskipTests"
                }
            }
        }
        /*stage('Test') {
            steps {
                dir('BackendofADEIVotechain') {
                    sh "./mvnw test"
                }
            }
        }*/
        stage('Deploy-Backend') {
            steps {
                dir('BackendofADEIVotechain') {
                    // Construire l'image Docker en spécifiant le chemin du Dockerfile
                    sh "docker build -t my-backend-2 ."
                    
                    // Se connecter à Docker Hub
                    sh "docker login -u hamzalambara -p plazma235"
                    
                    // Récupérer l'image existante (si nécessaire)
                    sh "docker pull hamzalambara/adeivotechain-1:my-backend-2"
                    
                    // Pousser l'image vers Docker Hub
                    sh "docker push hamzalambara/adeivotechain-1:my-backend-2"
                }
            }
        }
    }
}

