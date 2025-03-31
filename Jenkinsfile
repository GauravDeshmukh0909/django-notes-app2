@Library("Shared") _

pipeline{
    agent {label 'First_Agent'}
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps {
                script {
                    clone("https://github.com/GauravDeshmukh0909/django-notes-app2.git", "main") // ✅ Fixed function call
                }
            }
        }
        stage("Build"){
            steps{
                echo "this is Building stage"
                bat "docker compose up -d"
                
            }
        }
        stage("Test"){
            steps{
                echo "this is testing stage"
            }
        }
        stage("Push to docker hub"){
            steps{
                
                
                echo "Pushing the image to Docker Hub..."
                script{
                    docker_push("dockerHubCred","notes-app")
                }
                
                
                
                
            }
        }
        stage("Deploy"){
            steps{
                echo "this is deploying stage"
                bat "docker run -d -p 7000:8000 notes-app:latest"
            }
        }
    }
}
