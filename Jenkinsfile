pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('run code-analysis') {
            steps{
                sh"/opt/soanar/bin/sonar-scanner"
            }
             
           
        }
    }
}