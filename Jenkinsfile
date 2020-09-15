pipeline {
   agent any
   stages {
    stage('Checkout') {
      steps {
        script {
           // The below will clone your repo and will be checked out to master branch by default.
           git credentialsId: 'pradeep-puttarajaiah-jdas', url: 'https://github.com/pradeep-puttarajaiah-jdas/helm-test.git'
           // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
           sh "ls -lart ./*" 
           // Update repo
           sh 'helm repo update'
           // Linting
           sh 'helm lint mychart'
           // Application Deployment 
           sh 'helm install test_chart mychart -n chart-test'
           // Chart testing
           sh 'helm test test_chart -n chart-test'
           sh 'kubectl describe pod mychart'
          }
       }
    }
  }
}
