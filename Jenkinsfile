pipeline{
  agent any
  stages{
    stage("Checkout"){
      steps{
          git 'https://github.com/chaitanyajoshi27/maven-project.git'
      }
    }
    stage("Package"){
      steps{
        withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
        sh 'mvn clean package'
        }
      }
    }
    stage("Deploy"){
      steps{
        sshagent(['TomcatKey']) {
          sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@13.232.209.14:/usr/share/tomcat/webapps'
        }
      }
    }    
  }
}