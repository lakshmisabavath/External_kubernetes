pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                echo 'Build docker image'
                bat 'docker build -t kubedemoapp .'
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
                bat 'docker tag kubedemoapp:v1 sabavathlakshmi/sample:t1'
                bat 'docker push sabavathlakshmi/sample:t1'
            }
        }
        stage('Deploy'){
            steps{
                bat 'kubectl apply -f deployment.yaml --validate=false --insecure-skip-tls-verify'
                bat 'kubectl apply -f service.yaml --insecure-skip-tls-verify'
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
