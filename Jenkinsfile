pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                    kubectl apply -f deployment.yaml
                    kubectl apply -f service.yaml
                    kubectl apply -f hpa.yaml
                    kubectl apply -f ingress.yaml
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                    kubectl rollout status deployment/spring-petclinic --timeout=120s
                    kubectl get pods -o wide
                    kubectl get svc
                '''
            }
        }
    }
}
