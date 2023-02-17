pipeline {
    agent any 
    
    stages {
        stage('Compile and Clean') { 
            steps {
               sh "mvn clean compile"
            }
        }
        stage('deploy') { 
            
            steps {
                sh "mvn package"
            }
        }
        stage('Build Docker image'){
          
            steps {
                
                sh 'docker build -t  akashthavare18/deploy-container:${BUILD_NUMBER} .'
            }
        }
        
        stage('Docker deploy'){
            steps {
               
                sh 'docker run -itd -p  8082:8080 akashthavare18/deploy-container:${BUILD_NUMBER}'
            }
        }
        stage('Archving') { 
            steps {
                 archiveArtifacts '**/target/*.jar'
            }
        }
    }
}


