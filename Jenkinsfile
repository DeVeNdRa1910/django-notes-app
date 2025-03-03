@Library('Shared') _

pipeline{
    
    agent { label 'vinod' }
    
    stages{
        
        stage('Say Hello'){
            steps{
                script{
                    hello()   
                }
            }
        }
        
        stage('Code'){
            steps{
                echo 'Start cloning the code from github'
                script{
                    clone("https://github.com/DeVeNdRa1910/django-notes-app.git/", "main")
                }
            }
        }
        stage('Build the image') {
            steps {
                script{
                    docker_build("notes-app", "latest")
                }
            }
        }
        stage('Pushing the image on dockerHub') {
            steps {
                echo 'Start pushing image on dockerhub'
                script{
                    push_Docker_Image('notes-app', 'latest')
                }
            }
        }
        stage('Test'){
            steps{
                script{
                    test()
                }
            }
        }
        stage('Deploy'){
            steps{
                script{
                    run_Docker_Compose_File()
                }
            }
        }
    }
}
