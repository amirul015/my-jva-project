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
                 withDockerRegistry([credentialsId: 'docker_cred', url: 'https://hub.docker.com/repository/docker/amirul135/']) {
                    sh "docker build -t my-docker-repo/app:latest ."
                    sh "docker push my-docker-repo/app:latest"
                  }
               }   
           } 
       }
    }
}    
