node{
   stage('SCM Checkout'){
     git 'https://github.com/snagarajudmm/my-app.git'
   }
 stage('Compile'){
      // Get maven home path
     // def mvnHome =  tool name: 'maven-3', type: 'maven'
      sh "${mvnHome}/bin/mvn compile"
    }
 }
 stage('SonarQube Analysis') {
       // def mvnHome =  tool name: 'maven-3', type: 'maven'
        withSonarQubeEnv('sonarqube-6.7.6') {
          sh "${mvnHome}/bin/mvn sonar:sonar"
        }
  stage('test'){
      // Get maven home path
     // def mvnHome =  tool name: 'maven-3', type: 'maven'
      sh "${mvnHome}/bin/mvn compile"
    }
    {
    junit 'target\\surefire-reports\\*.xml'
   }
  stage('package'){
      // Get maven home path
     // def mvnHome =  tool name: 'maven-3', type: 'maven'
      sh "${mvnHome}/bin/mvn compile"
    }
    }
