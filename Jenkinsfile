pipeline {
  agent {
    
    node { 
      label 'ghost20'
      customWorkspace '/home/ingestion-5gcs/artifacts-test'
      }
    stages {
      stage('Git Checkout') {
        steps {
          echo "Begin checkout of the git project"
        }
      }
    }
  }
}
