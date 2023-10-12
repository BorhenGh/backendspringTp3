pipeline {
    agent any 
    tools { 
        maven 'maven'
    }
    stages {
        stage ("Clean up"){
            steps {
                deleteDir()
            }
        }
        stage ("Clone repo"){
            steps {
                sh "git clone https://github.com/BorhenGh/backendspringTp3.git"
            }
        }
        stage ("Generate backend image") {
              steps {
                   dir("backendspringTp3"){
                      sh "mvn clean install"
                      sh "docker build -t doctp3-spring ."
                  }                
              }
          }
        stage ("Run docker compose") {
            steps {
                 dir("backendspringTp3"){
                    sh " docker compose up -d"
                }                
            }
        }
    }
}
