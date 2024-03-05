pipeline{
    agent any
        stages{
            stage("k8s"){
                steps{
                    withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'cluster', contextName: '', credentialsId: 'jenkins', namespace: 'default', serverUrl: 'https://CA37CE954E47CBE48FBA49185D7009C1.yl4.eu-west-2.eks.amazonaws.com']]) 
                    {
                    sh 'curl -LO "https://storage.googleapis.com/kubernetes-release/release/v1.20.5/bin/linux/amd64/kubectl"'
                    sh 'chmod u+x ./kubectl'
                    sh './kubectl get nodes'
                    sh './kubectl create -f mytriotaskflaskapp-deployment.yaml'
                    sh './kubectl create -f mytriotaskflaskapp-service-deployment.yaml'                    
                    sh './kubectl get pods'
                    }
                }    
        }
    }
}
