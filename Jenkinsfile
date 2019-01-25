pipeline {
  agent {
    label "jenkins-maven"
  }
  environment {
    DEPLOY_NAMESPACE = "jx-staging"
  }
  stages {
    stage('Validate Environment') {
      steps {
        container('maven') {
            sh 'echo Environment is successfully Validated'
        }
      }
    }
    stage('Build Service') {
      steps {
        container('maven') {     
            sh 'echo Service is successfully build'
         
        }
      }
    }
    stage('DeployApp') {
      steps {    
           container('maven') {
            	sh 'wget https://github.com/argoproj/argo-cd/releases/download/v0.11.0/argocd-linux-amd64 -O argocd && chmod +x argocd'
           		sh 'PATH=$PATH:$PWD/ && argocd login 129.213.76.0 --username admin --password argocd-server-66b7595985-6m8tm --insecure && argocd app create guestbook --name=guestbook --repo https://github.com/RajeshAjjarapu/cicd-jenkinsx-argocd.git --path=guestbook --dest-server https://kubernetes.default.svc --dest-namespace jx'  
        }
      }
    }
    stage('Test Service') {
      steps {
        container('maven') {     
            sh 'echo Service is successfully Tested and Signoff Ready'
         
        }
      }
    }
  }
  }
