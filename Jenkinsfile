pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-scon', namespace: 'webapps', serverUrl: 'https://C7B71927EEE832F38DA06525F3EC9F5F.yl4.eu-west-1.eks.amazonaws.com']]) {
                 sh 'kubectl apply -f deployment-service.yml'
                }
            }
        }
        
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-scon', namespace: 'webapps', serverUrl: 'https://C7B71927EEE832F38DA06525F3EC9F5F.yl4.eu-west-1.eks.amazonaws.com']]) {
                 sh 'kubectl get svc -n webapps'
                }
            }
        }
    }
}
