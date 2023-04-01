pipeline{
    agent any
    environment {
        PATH = "$PATH:/root/.dotnet/tools"
    }
    stages{
               
       stage('Build'){
            steps{
                sh 'export PATH="$PATH:/root/.dotnet/tools"'
                sh 'cd /var/lib/jenkins/workspace/trial/'
                sh 'dotnet sonarscanner begin /k:"poc6-auth" /d:sonar.host.url="http://35.225.86.148:9000"  /d:sonar.login="sqp_87bc636c842a09d39b0aedd4e9f061d34b3dc10f"'
                sh 'dotnet build'
            }
         }
        stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        withSonarQubeEnv('sonarqube-9.9') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
        sh 'dotnet sonarscanner end /d:sonar.login="sqp_87bc636c842a09d39b0aedd4e9f061d34b3dc10f"'
    }
        }
        }
       
    }
}
