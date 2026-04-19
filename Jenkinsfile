pipeline
{ 
    agent any
stages
{ 
    stage('Code')
    {
        steps
    { 
        git branch: 'main', url: 'https://github.com/3432sdffsdd/flask-app.git'
        }
        }
        stage('Build') 
        {
            steps
            { sh 'docker build -t flask-app:latest .'
            }
            }
        stage('Docker Compose Build')
        {
            steps 
            { 
                sh 'docker compose build'
                } 
            
        }
            stage('Docker Compose run')
            {
                steps 
                {
                    sh 'docker compose up -d' 
                    
                }} } }
