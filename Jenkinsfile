pipeline {
    agent any
    
    stages {
        stage('Git Checkout') {
           steps {
               git branch: 'main', url: 'https://github.com/amirul015/my-jva-project'
           } 
        }
        stage('Compile') {
           steps {
               sh 'mvn clean package'
           } 
        }
        stage('Docker Build & push') {
           steps {
             script {  
                 withDockerRegistry(credentialsId: 'docker_cred') {
                    sh "docker build -t amirul135/app:latest ."
                    sh "docker push amirul135/app:latest"
                  }
               }   
           } 
       }
    }
}    
