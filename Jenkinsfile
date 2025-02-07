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
                sh 'kubectl apply -f deployment.yaml'
            }
        }
        stage('service') {
            steps {
                echo 'checkout'
                sh 'kubectl apply -f service.yaml'
            }
        }
        stage('Config-map') {
            steps {
                echo 'checkout'
                sh 'kubectl create configmap my-webapp-html --from-file=index.html'
            }
        }
        stage('get_deployment') {
            steps {
                echo 'checkout'
                sh 'kubectl get deployment -n test'
                sh 'kubectl describe deployment my-webapp -n test'
            }
        }
        stage('get_service') {
            steps {
                echo 'checkout'
                sh 'kubectl get svc -n test'
                sh 'kubectl describe svc my-webapp-service -n test'
            }
        }
        stage('get_configmap') {
            steps {
                echo 'checkout'
                sh 'kubectl get cm -n test'
                sh 'kubectl describe cm my-webapp-html -n test'
            }
        }
    }
}
