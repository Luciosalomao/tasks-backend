pipeline {
    agent any
    stages {
        stage ('Build Backend') {
            steps {
                bat 'mvn clean package -DskipTests=true'
            }
        }
        stage ('Sonar Analysis') {
            environment {                
                scannerHome = tool 'SONAR_SCANNER'
            }            
            steps {
                withSonarQubeEnv('SONAR_LOCAL') {
                    bat "${scannerHome}/bin/sonar-scanner -e -Dsonar.projectKey=DeployBack -Dsonar.host.url=http://localhost:9000 -Dsonar.login=sqa_6ebd4f32a47c668b82dfb27586b09213ca956d16 -Dsonar.java.binaries=target"
                }                
            }
        }
    }
}

