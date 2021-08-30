pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('Checkout SCM'){
            steps{
                git url: 'https://github.com/akshitttt/Jenkins_Spring.git'
            }
        }
        stage('Build Docker'){
            steps{
                sh 'mvn clean'
                sh 'mvn install'
                sh 'mvn package'
                sh 'docker-compose build'
                sh 'docker-compose up -d'
            }
	}
}
