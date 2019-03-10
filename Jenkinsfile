pipeline {
   
      agent {
           docker {
                script{
                  def dockerHome = tool 'my_docker'
                  env.PATH = "${dockerHome}/bin:${env.PATH}"
                }
              image 'node:carbon'
              args '-p 3000:3000'
             }

    stages {
        
        stage('Initialize'){
        steps{
            script{
             def dockerHome = tool 'my_docker'
             env.PATH = "${dockerHome}/bin:${env.PATH}"
            }
            
    }
        }
    }
        stage ('Build') {
           
            steps {
                                
                sh 'npm config ls'
                    
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
    
