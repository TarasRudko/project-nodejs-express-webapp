pipeline {
    agent {
        docker {
            image 'node:carbon'
            args '-p 3000:3000'
        }
    }

    stages {
        stage ('Build') {
           
            steps {
                                
               // sh 'sudo npm install'
                    
                }
            }
        
        stage('Push Docker Image') {
            when {
                branch 'master'
            }
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_login') {
                        app.push("${env.BUILD_NUMBER}")
                        app.push("latest")
                    }
                }
            }
        }
    }
        
}
    
