pipeline {
  agent any
  parameters {
    choice(name: 'Continue',
      choices: 'Yes\nNo',
      description: 'Do you want to continue')
    choice(name: 'Stop_Engine',
      choices: 'Yes\nNo',
      description: "Stop the engine Yes or No")      
  }
  
  stages {
    stage('Example') {
      steps {
        echo 'Hello World'
        echo "Your choice: ${params.Continue}"
	echo 'Do You want to stop the engine'
	echo "Your choice is ${params.Stop_Engine}"
        }
     }
  }
}
