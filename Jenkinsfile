node {
        properties([
                parameters([
                choice(name: 'Continue', choices: 'Yes\nNo', defaultValue: 'No', description: "Do you want to continue"),
                ])
        ])

        stage('Git Checkout') {

              echo "Begin checkout of the git project"
                echo "${params.Continue}"

          }
        }
