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
             scripts {  
                 withDockerRegistry([credentialsId: 'docker_cred', url: 'https://app.docker.com/]) {
                    sh "docker build -t my-docker-repo/app:latest ."
                    sh "docker push my-docker-repo/app:latest"
                  }
               }   
           } 
       }
    }
}    
