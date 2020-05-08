node {
      def remote = [:]
      remote.name = 'OCP-Tester'
      remote.host = "${params.SUT_HOST}"
      remote.user = "${params.SUT_USER}"
      remote.password = "${params.SUT_PASSWORD}"
      remote.allowAnyHosts = true
      def checkout_dir = "${params.CHECKOUT_DIR}"
        
        properties([
                parameters([
                choice(name: 'Continue', choices: 'Yes\nNo', defaultValue: 'No', description: "Do you want to continue"),
                string(name: 'CHECKOUT_DIR', defaultValue='artifacts_test', description: 'Checkout directory'),
                string(name: 'SUT_HOST', defaultValue='ghost20.gre.hpecorp.net', description: 'SUT Host info'),                       
                string(name: 'SUT_USER', defaultValue='ingestion-5gcs', description: 'SUT username'),
                string(name: 'SUT_PASSWORD', defaultValue='ingestion-5gcs', description: 'SUT password'),
                string(name: 'CHARTS_LIST', defaultValue='hpe-nf-udm', description: 'CHARTS List'),
              ])
        ])

        stage('Git Checkout') {

              echo "Begin checkout of the git project"
              echo "${params.Continue}"
              checkout_dir=${params.CHECKOUT_DIR}
              dir ("${checkout_dir}") {
                checkout scm
              }
              sshPut remote: remote, from: "${checkout_dir}", into: '.'
              sshCommand remote: remote, command: "cd ${checkout_dir}/; sh test.sh ${params.CHARTS_LIST}"
          }
}
