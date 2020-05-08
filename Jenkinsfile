node {
        parameters {
          choice(name: 'Continue',
          choices: 'Yes\nNo',
          defaultValue: 'Yes',
          description: 'Do you want to continue')
        }
        stage('Git Checkout') {

              echo "Begin checkout of the git project"
                echo "${params.Continue}"

          }
        }
