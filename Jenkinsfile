node{
   stage('SCM Checkout'){
     git 'git credentialsId: 'Git-credentials', url: 'https://github.com/snagarajudmm/myweb.git'
   }
 stage('Compile the code'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'
      sh "${mvnHome}/bin/mvn compile"
    }
 }
 stage('SonarQube Analysis') {
        def mvnHome =  tool name: 'maven-3', type: 'maven'
        withSonarQubeEnv('sonarqube-6.7.6') {
          sh "${mvnHome}/bin/mvn sonar:sonar -Dsonar.host.url=http://3.83.11.199:9000
        }
  stage('test'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'
      sh "${mvnHome}/bin/mvn test"
    }
    {
    junit 'target\\surefire-reports\\*.xml'
   }
  stage('package'){
      // Get maven home path
     def mvnHome =  tool name: 'maven-3', type: 'maven'
      sh "${mvnHome}/bin/mvn package"
    }
    }
