pipeline {

  agent { label 'kubeconfig' }

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/shiva6933/minikube.git', branch:'master'
      }
    }

    stage('Deploy App') {
      steps {
        script {
          withCredentials([file(credentialsId: 'kubeconfig', variable: 'KUBECONFIG')])
        }
      }
    }

  }

}
