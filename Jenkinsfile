pipeline{
  agent any
  stages{
    stage("Checkout"){
      steps{
          git 'https://github.com/chaitanyajoshi27/maven-project.git'
      }
    }
    stage("Compile"){
      steps{
        
      }
    }
    stage("Build"){
      steps{
        withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
        sh 'mvn package'
        }
      }
    }
  }
}