node {
      def remote = [:]
      remote.name = 'OCP-Tester'
      remote.host = "${params.SUT_HOST}"
      remote.user = "${params.SUT_USER}"
      remote.password = "${params.SUT_PASSWORD}"
      remote.allowAnyHosts = true
      
        
      properties([
            parameters([
                choice(name: 'Continue', choices: 'Yes\nNo', defaultValue: 'No', description: "Do you want to continue"),
                string(name: 'CHECKOUT_DIR', defaultValue:'artifacts_test', description: 'Checkout directory'),
                string(name: 'SUT_HOST', defaultValue:'ghost20.gre.hpecorp.net', description: 'SUT Host info'),                       
                string(name: 'SUT_USER', defaultValue:'ingestion-5gcs', description: 'SUT username'),
                string(name: 'SUT_PASSWORD', defaultValue:'ingestion-5gcs', description: 'SUT password'),
                string(name: 'CHARTS_LIST', defaultValue:'hpe-nf-udm', description: 'CHARTS List'),
                      ])
      ])        

        stage('Git Checkout') {

              echo "Begin checkout of the git project"
              echo "${params.Continue}"
              checkout_dir = "${params.CHECKOUT_DIR}"
              dir ("${checkout_dir}") {
                checkout scm
              }
              sshPut remote: remote, from: "${checkout_dir}", into: '.'
              sshCommand remote: remote, command: "cd ${checkout_dir}/; sh test.sh ${params.CHARTS_LIST} ${params.SUT_HOST} ${BUILD_NUMBER}"
              def new_exclude_patterns = [[pattern: "reports-*/**", type: 'EXCLUDE']]
              cleanWs deleteDirs: true, skipWhenFailed: true, patterns: new_exclude_patterns
              sshRemove remote: remote, path: "/tmp/reports"
              sshRemove remote: remote, path: "${CHECKOUT_DIR}"
          }
      
          stage('Reports archival on remote node') {
            // Cleanup SUT
            echo "=========================================================================="
            echo "Archival of reports on remote node"
            echo "=========================================================================="
              
            sleep 1
            sshCommand remote: remote, command: 'echo "Reports collection is in progress"'
            //sshCommand remote: remote, command: "cd ${checkout_dir}/src/5GCS-nf/; sh reportsArchive.sh ${params.CHARTS_LIST} ${BUILD_NUMBER} ${params.NF_REPORT_PATH} ${params.NF_CUSTOMIZED_FILES_PATH}"
            sshGet remote: remote, from: '/home/ingestion-5gcs/iot-test/destinations/report-1171-hpe-nf-udm---OPENSHIFT.report', into: '/var/lib/jenkins/workspace/my-test', override: true
    }
}
