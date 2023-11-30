pipeline{
    agent any
    stages{
        stage('git checkout'){
            steps{
                git credentialsId: 'git_credentials', url: 'https://github.com/leoc3120/devops5.git'
                
            }
        }
        stage('Build the aplication'){
            steps{
                sh 'mvn clean install'
            }
        }
        stage('Unit test Execution'){
            steps{
                sh 'mvn test'
            }
        }
        stage('Build the docker image'){
            steps{
                withCredentials([string(credentialsId: 'dockerhubpass', variable:'dockerHubPass')]){
                sh "docker login -u leoc3120 -p $dockerHubPass"
                }
                sh 'docker build -tagleoc3120/redis:latest'
            }
        }
    }
}
