pipeline {
  agent any
  parameters {
<<<<<<< HEAD
    choice(name: 'Continue',
=======
    choice(name: "Continue \'Yes\' or \'No\' ",
>>>>>>> 5e233180527134143444ac93c95a029f9f5f725d
      choices: 'Yes\nNo',
      description: 'Do you want to continue')
  }
  stages {
    stage('Example') {
      steps {
        echo 'Hello World'
        echo "Your choice: ${params.Continue}"
        }
     }
  }  
}

