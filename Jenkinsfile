pipeline{
    agent any
    environment {
        PATH = "$PATH:/root/apache-maven-3.9.6/bin"
    }
    stages{
       stage('Checkout'){
            steps{
                git 'git@github.com:NagiReddyDEVOPS/Sonar-Project.git'
            }
         }        
       stage('Package'){
            steps{
                sh 'mvn clean package'
            }
         }
        stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        withSonarQubeEnv('sonarqube') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
        sh "mvn clean verify sonar:sonar -Dsonar.projectKey=sonarproject -Dsonar.host.url=http://52.66.143.134:9000 -Dsonar.login=sqp_dba14b0f84029fbaa9680cc5b5a68b19e6a37a0e"
    }
        }
        }
       
    }
}
