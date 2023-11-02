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

            stage('Build on k8 ') {
            steps {
              sh 'pwd'
              sh 'cp -R helm/* .'


           
                }  

            }
     }
   }    