node{
   stage('SCM Checkout'){
     git 'git credentialsId: 'Git-credentials', url: 'https://github.com/snagarajudmm/myweb.git'
 stage('Compile the code'){
      // Get maven home path
      sh  "mvn compile"
    }
 stage('SonarQube Analysis') {
 
        {
          sh "mvn sonar:sonar" 
        }
  stage('test'){
     
      sh "mvn test"
    }
  stage('package'){
      
      sh "mvn package"
    }
    }
