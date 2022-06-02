pipeline {
    agent any
    
    environment {
    registry = '259289693704.dkr.ecr.us-east-1.amazonaws.com/devops_repository'
    registryCredential = 'jenkins-ecr'
    dockerimage = ''
  }
    
        stage('Build Image') {
            steps {
                script{
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                } 
            }
        }
        stage('Deploy image') {
            steps{
                script{ 
                    docker.withRegistry("https://"+registry,"ecr:us-east-1:"+registryCredential) {
                        dockerImage.push()
                    }
                }
            }
 }
