pipeline {
    agent { label 'dev-agent' }
    
    stages{
        stage('Code'){
            steps {
                git url: 'https://github.com/pawardhiraj561/dspgit-.git', branch: 'master'
            }
        }
        stage('Build and Test'){
            steps {
                sh 'docker build . -t trainwithshubham/node-todo-app-cicd:latest' 
            }
        }
        stage('Login and Push Image'){
            steps {
                echo 'logging in to docker hub and pushing image..'
                withCredentials([usernamePassword(pawardhiraj998@gmail.com:'dockerHub',passwordVariable:'admin@998  ', usernameVariable:'pawar199813')]) {
                    sh "docker login -u ${env.pawar199813'} -p ${env.admin@998}"
                    sh "docker push trainwithshubham/node-todo-app-cicd:latest"
                }
            }
        }
        stage('Deploy'){
            steps {
                sh 'docker-compose down && docker-compose up -d'
            }
        }
    }
}
