pipeline {
    agent any 
    
    stages {
        stage('Clean') { 
            steps {
               sh 'mvn clean'
            }
        }
        stage('deploy') { 
            
            steps {
                sh "mvn package"
            }
        }
        stage('Build Docker image'){
          
            steps {
                
                sh 'docker build -t  akashthavare/deploy-container:${BUILD_NUMBER} .'
            }
        }
        
        stage('Docker deploy'){
            steps {
               
                sh 'docker run -itd -p  8082:8080 akashthavare/deploy-container:${BUILD_NUMBER}'
            }
        }
        stage('Archving') { 
            steps {
                 archiveArtifacts '**/target/*.jar'
            }
        }
    }
}


