pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MY-EKS-one', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8A814FAAC4963BEE67BE09DCFDBE618E.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MY-EKS-one', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8A814FAAC4963BEE67BE09DCFDBE618E.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
