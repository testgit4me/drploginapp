pipeline {
    agent {
       node {
         label "valaxy"
      }
    }
    stages {
        stage('Build') {
            steps {
		changes done via developer 1
                echo '<--------------- Building started --------------->'
                sh 'printenv'
                sh 'mvn clean install'
                echo '<------------- Build completed --------------->'
            }
        }

  stage ("Sonar Analysis") {
            environment {
               scannerHome = tool 'Valaxy-SonarScanner'  //scanner name configured for slave 
            }
            steps {
                echo '<--------------- Sonar Analysis started  --------------->'
                withSonarQubeEnv('Valaxy-SonarQube') {    
                    //sonarqube server name in master
                    sh "${scannerHome}/bin/sonar-scanner"
                }    
                echo '<--------------- Sonar Analysis stopped  --------------->'
            }   
        }
    }
}
