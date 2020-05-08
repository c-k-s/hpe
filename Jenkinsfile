pipeline {
  agent {
    node {
      
      def remote = [:]
      remote.name = 'OCP-Tester'
      remote.host = "${params.SUT_HOST}"
      remote.user = "${params.SUT_USER}"
      remote.password = "${params.SUT_PASSWORD}"
      remote.allowAnyHosts = true  
  
      parameters {
        choice(name: 'Continue',
          choices: 'Yes\nNo',
          description: 'Do you want to continue')
        choice(name: 'Stop_Engine',
          choices: 'Yes\nNo',
          description: "Stop the engine Yes or No")
        string(name: 'CHECKOUT_DIR',
          defaultValue: 'artifacts_IOT',
          description: "This is the default checkout directory")
        string(name: 'CHARTS_LIST',
          defaultValue: 'hpe-nf-udm hpe-sde-udr',
          description: "Default charts list")
        string(name: 'SUT_HOST',
          defaultValue: '15.112.154.46',
          description: "Default SUT HOSTNAME")
        string(name: 'SUT_USER',
          defaultValue: 'root',
          description: "Default SUT USERNAME")
        string(name: 'SUT_PASSWORD',
          defaultValue: 'hwroot',
          description: "Default SUT PASSWORD")
      }

        stages {
    
          def checkout_dir = ${params.CHECKOUT_DIR}
          def charts_list = ${params.CHARTS_LIST}
          stage('Git Checkout') {
            steps {
              echo "Begin checkout of the git project"
              def new_exclude_patterns = [[pattern: "reports-*/**", type: 'EXCLUDE']]
              cleanWs deleteDirs: false, skipWhenFailed: false, patterns: new_exclude_patterns
        
              dir ("${checkout_dir}") {
                checkout scm
                }
              sshPut remote: remote, from: "${checkout_dir}", into: '.'
              }
            }
    
          stage('Example') {
            steps {
              echo 'Hello World'
              echo "Your choice: ${params.Continue}"
              }
            }
  
          stage('Engine stop') {
            steps {
              echo "Do you want to stop the engine ? "
              echo "Your choice is ${params.Stop_Engine}"
              }
            }
  
          stage('Chart download') {
            steps {
              echo "The charts list is : ${params.CHARTS_LIST}"
              sshCommand remote: remote, command: "cd ${checkout_dir}/src/5GCS-nf/; sh test.sh ${charts_list}"
              }
            }
        }
    }
  }
}
