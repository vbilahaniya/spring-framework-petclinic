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
                //clean before run 
                cleanws()
                sh"${scannerHome}/bin/sonar-scanner"
            }
             
           
        }
    }
}