pipeline {
    agent any
    stages{
        stage("git"){
            steps{
                git 'https://github.com/jackysedy/python-app'
                sh """
                    whoami
                    docker build -t python-app .
                    docker images
                    curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.20.4/2021-04-12/bin/linux/amd64/kubectl
                    chmod +x ./kubectl
                    mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin
                    echo 'export PATH=$PATH:$HOME/bin' >> ~/.bashrc
                     export AWS_ACCESS_KEY_ID=AKIAQ5XLUSRQBJER5THL
                     export AWS_SECRET_ACCESS_KEY=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
                     export AWS_DEFAULT_REGION=us-east-1
                    
                    
                    aws eks update-kubeconfig --region us-east-1 --name jacky
                    kubectl get nodes
                    cd Helm
                    /usr/local/bin/helm upgrade python-app .
                """
            }
        }
    }
}
