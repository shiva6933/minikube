pipeline {

  agent { label 'kubepod' }

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/shiva6933/minikube.git', branch:'master'
      }
    }

    stage('Deploy App to Kubernetes') {     
      steps {
        container('kubectl') {
          withCredentials([file(credentialsId: 'kubeconfig', variable: 'KUBECONFIG')]) {
            sh 'sed -i "s/<TAG>/${BUILD_NUMBER}/" myweb.yaml'
            sh 'kubectl apply -f myweb.yaml'
          }
        }
      }
    }

  }

}
