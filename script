pipeline{
    agent any
    stages{
        stage('deploy'){
            steps{
                script{
                    sshagent(['k8s']) {
                        sh 'rm -rf k8s'
                        sh "git clone https://github.com/chris-reeves1/k8s"
                        sh 'scp -o StrictHostKeyChecking=no k8s/deployment.yaml ubuntu@3.8.82.115:/tmp/deployment.yaml'
                        sh """
ssh -o StrictHostKeyChecking=no ubuntu@3.8.82.115 'export PATH=$PATH:/home/ubuntu/bin && KUBECONFIG=~/.kube/config kubectl apply -f /tmp/deployment.yaml'
"""



                    }

                }
            }
        }
    }
}
