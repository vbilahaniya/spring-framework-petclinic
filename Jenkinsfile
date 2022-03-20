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
          stage("codeAnalysis"){
            environment {
              def sonarHome = tool name: 'SonarQube-Scanner 2.4'
            }
            steps {  
                withSonarQubeEnv('SonarScanner') {
                    sh "${sonarHome}/opt/sonar-scanner"
                }
                sleep time: 30000, unit: 'MILLISECONDS'
                script {
                        def qg = waitForQualityGate()
                        if (qg.status != 'OK') {
                            error "Pipeline aborted due to quality gate failure: ${qg.status}"
                        }
                   }
            }
        }
    }
}