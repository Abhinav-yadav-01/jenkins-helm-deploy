pipeline {
    agent any
        stages{
            stage('Build maven'){
                steps{
                    sh 'pwd'
                    sh 'mvn clean install package'
                }
            }
            stage('Copy Artifacts'){
                steps{
                    sh 'pwd'
                    sh 'cp -r target/*.jar docker'
                }
            }
            stage('Run Test'){
                steps{
                    sh 'mvn test'    
                }
            }
            stage('Build docker Image and Push Image'){
                steps{
                    script{
                        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
                        def customImage = docker.build("abhionedocker/petclinic:${env.BUILD_NUMBER}", "./docker/Dockerfile")
                         customImage.push()
                    }
                }
            }
            
        }
}
