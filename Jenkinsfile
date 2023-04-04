pipeline {
    agent {
        node {
            label 'java11'
        }
    
    }

    options {
                timestamps()
                buildDiscarder(logRotator(numToKeepStr: '5', artifactNumToKeepStr: '2'))
                timeout(time: 240, unit: 'MINUTES')
               // disableConcurrentBuilds()
                }

        stages {
            stage ('AppCodeCheckout') {
                steps {

                    git 'https://github.com/varunraj24/Devops-Git-Maven.git'

                }
            }
            stage ('CI Build') {

                steps {

                    sh 'mvn clean package'
                   
                     }
    
            }

            stage ('Docker Build && Push && DEPLOY ') {
               

                steps {
                    
                    sh 'docker build . -t varunraj25/app13:test'
                    sh 'docker login -u varunraj25 -p dckr_pat__43Z1MAoTSoPf8AJhVgj8KaQlrA'
                    sh 'docker push varunraj25/app13:test'
                    sh 'docker run -p 86:8080 -d varunraj25/app13:test'

                }
            
        }


            }
        }  
