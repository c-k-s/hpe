node{
  stage('SCM Checkout'){
     git 'https://github.com/c-k-s/hpe.git'

   }
  stage('Compile-Package'){
    sh 'mvn package'
   }
}
