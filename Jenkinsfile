pipeline {
    agent any
        stages {
            stage("Building SONAR ...") {
               steps {
                   bat '''
                       cd worker
                       mvn clean install
                       '''
                    }
                }

            stage('SonarQube') {
            steps{
                bat '''
                    cd worker
                   mvn sonar:sonar \
                            -Dsonar.projectKey=d8a093e3afba7618938beee258cd18d4cdf799edd8a093e3afba7618938beee258cd18d4cdf799ed \
                            -Dsonar.host.url=http://localhost:9000 \
                            -Dsonar.login=d9f37ae127b215b2b2f5ddeed09cc3c47dd0930f
                '''
            } 
        }
            // Build The Project              
            stage('Build') {
                    tools {	
        			    jdk 'JDK 1.8'
        			    maven 'Maven_install'
        	         }
                         steps {
                             git 'https://github.com/Neha2602/voting_app.git'
                           bat '''
                           cd worker
                            java -version
            			    mvn -version
            			    mvn clean package
                            mvn clean install
                           '''
                         }
        }
       
  }      
}
