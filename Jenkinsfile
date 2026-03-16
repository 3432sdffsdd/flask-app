pipeline {
    agent any
    
    stages {
        stage("Code") {
            steps {
                git url: 'https://github.com/yo-its-anas/flask-app.git', branch: 'main'
            }
        }
        stage("Build") {
            steps {
                sh "docker build -t flask-app:latest ."
            }
        }
        stage("Push to Docker Hub") {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerHubCreds',
                    usernameVariable: 'dockerHubUser',
                    passwordVariable: 'dockerHubPass'
                )]) {
                    sh 'docker login -u $dockerHubUser -p $dockerHubPass'
                    sh 'docker image tag flask-app:latest $dockerHubUser/flask-app:latest'
                    sh 'docker push $dockerHubUser/flask-app:latest'
                } 
            }
        }
        stage("Deployment") {
            steps {
                sh "docker-compose down"
                sh "docker-compose up -d"
            }
        }
    }
}
