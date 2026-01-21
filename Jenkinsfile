pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'macha-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://81C1B8038F2DC342ED3FBA5D26EEE8D2.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'macha-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://81C1B8038F2DC342ED3FBA5D26EEE8D2.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
