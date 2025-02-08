pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Marypearl/elections-result.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t elections-result-app .'
            }
        }
        stage('Deploy Container') {
            steps {
                sh 'docker run -d --name elections-result-app --network front-tier -p 5001:80 elections-result-app'
                sh 'docker network connect back-tier elections-result-app'
            }
        }
    }
}



