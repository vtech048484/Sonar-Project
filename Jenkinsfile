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
        withSonarQubeEnv('SonarQube') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
        sh "mvn clean verify sonar:sonar -Dsonar.projectKey=Sonarqube -Dsonar.host.url=http://3.110.130.241:9000 -Dsonar.login=sqp_bfc26ad0b1952ea76c6e0bb118a2711b060113e3"
    }
        }
        }
       
    }
}
