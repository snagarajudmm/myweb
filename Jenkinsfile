node() {
stage('codecheckout'){
 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'GitHubCredentials', url: 'https://github.com/NagireddyGuduru/myweb.git']]])
}
def mvnHome = tool 'MAVEN_HOME'
def os = System.properties['os.name'].toLowerCase()
stage('compile'){

    echo "OS: ${os}"
    if (os.contains("linux")) {
      sh "mvn compile" 
    } else {
      bat "${mvnHome}/bin/mvn clean compile" 
    }
}
stage('test'){
    if (os.contains("linux")) {
      sh "mvn test" 
    } else {
      bat "${mvnHome}/bin/mvn clean test" 
    }
    junit 'target\\surefire-reports\\*.xml'
}
stage('package'){
    if (os.contains("linux")) {
      sh "mvn package" 
    } else {
      bat "${mvnHome}/bin/mvn clean package" 
    }
    archiveArtifacts 'target/*.war'
}
stage('deploy'){
    if (os.contains("linux")) {
        sh "sudo cp -f /var/lib/jenkins/workspace/pipeline/target/myweb.war /usr/local/tomcat7/webapps/" 
    } else {
      bat "copy F:\\JenkinsWorkspace\\workspace\\pipeline\\target\\myweb.war C:\\apache-tomcat-7.0.82\\webapps\\" 
    }
    
}
}
