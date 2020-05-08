pipeline {
  agent any
  parameters {
    choice(name: "Continue \'Yes\' or \'No\' ",
      choices: 'Yes\nNo',
      description: 'Do you want to continue')
  }
  stages {
    stage('Example') {
      steps {
        echo 'Hello World'
        echo "Your choice: ${params.choice}"
        }
     }
  }  
}

