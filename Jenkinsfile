@Library("Shared") _
pipeline {
    
    agent { label "ashish" }
    triggers {
        githubPush()
    }
    
    stages {
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage("Clone"){
            steps {
                script{
                    clone("https://github.com/emizentech38/django-notes-app.git" , "main" )
                }
            }
        }
         stage("Build"){
            steps {
                script{
                    build("notes-app" , "latest" , "emizentech38")
                }
            }
        }
         stage("Push To DockerHub"){
            steps {
                 script{
                     push("notes-app", "latest", "dockerHubCred")
                 }
            }
        }
         stage("Deploy"){
            steps {
                 echo "this is deploying the code"
                 sh "docker-compose down && docker-compose up -d"
            
            }
        }
    }
    
}
