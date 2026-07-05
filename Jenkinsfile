pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://60DCD34713A23845E6EC912F6EC336D9.sk1.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://60DCD34713A23845E6EC912F6EC336D9.sk1.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
