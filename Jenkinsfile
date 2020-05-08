pipeline {
  agent any
  parameters {
    choice(name: "Continue \'Y\' or \'N\' ",
      choices: 'Yes\n,No',
      description: 'Do you want to continue')
  }
  stages {
    stage('Example) {
      steps {
        echo 'Hello World'
        echo "Your choice: ${params.choice}"
        }
     }
  }  
}

