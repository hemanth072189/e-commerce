pipeline {
    agent any

    environment {
        KUBECONFIG = '/root/.kube/config'
    }
    stages {
        stage('scm') {
            steps {
                echo 'checkout'
            }
        }
        stage('deployment') {
            steps {
                echo 'checkout'
                sh 'sudo kubectl apply -f deployment.yaml'
            }
        }
        stage('service') {
            steps {
                echo 'checkout'
                sh 'sudo kubectl apply -f service.yaml'
            }
        }
        stage('Config-map') {
            steps {
                echo 'checkout'
                sh 'sudo kubectl create configmap my-snake-html --from-file=snake.html'
            }
        }
        stage('get_deployment') {
            steps {
                echo 'checkout'
                sh 'sudo kubectl get deployment -n test'
                sh 'sudo kubectl describe deployment my-webapp -n test'
            }
        }
        stage('get_service') {
            steps {
                echo 'checkout'
                sh 'sudo kubectl get svc -n test'
                sh 'sudo kubectl describe svc my-webapp-service -n test'
            }
        }
        stage('get_configmap') {
            steps {
                echo 'checkout'
                sh 'sudo kubectl get cm -n test'
                sh 'sudo kubectl describe cm my-webapp-html -n test'
            }
        }
    }
}
