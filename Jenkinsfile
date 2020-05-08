pipeline {
  agent {
    
    node { 
      label 'ghost20'
      customWorkspace '/home/ingestion-5gcs/artifacts-test'
      }
      def remote = [:]
      remote.name = 'OCP-Tester'
      remote.host = "${params.SUT_HOST}"
      remote.user = "${params.SUT_USER}"
      remote.password = "${params.SUT_PASSWORD}"
      remote.allowAnyHosts = true  
  
        stages {
    
          stage('Git Checkout') {
            steps {
              echo "Begin checkout of the git project"
              }
            }
    
          stage('Example') {
            steps {
              echo 'Hello World'
              }
            }
  
          stage('Engine stop') {
            steps {
              echo "Do you want to stop the engine ? "
              }
            }
  
         }
  }
