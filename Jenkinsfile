pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                echo 'Build docker image'
                bat 'docker build -t kubedemoapp:v1 .'
            }
        }
        stage('Login'){
            steps{
                echo 'Login to Docker Hub'
                bat 'docker login -u sabavathlakshmi -p Laxmi@Sabavath'
            }
        }
        stage('Push'){
            steps{
                echo 'Push docker image'
                bat 'docker tag kubedemoapp:v1 sabavathlakshmi/exmaple:t1'
                bat 'docker push sabavathlakshmi/example:t1'
            }
        }
        stage('Deploy'){
            steps{
                bat 'kubectl deploy apply -f deployment.yaml --validate=false'
                bat 'kubectl deploy apply -f service.yaml'

            }
        }
    }
        post{
            success{
                echo 'successfully finished'
            }
            failure{
                echo 'failed'
            }
        }
    }
