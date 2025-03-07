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
    stage("Create Docker Image"){
      steps{
        sh 'docker build -t chaitanyajoshi27/image918 .'
      }
    }    
    stage("Upload Image to DockerHub"){
      steps{
      withDockerRegistry(credentialsId: 'dockerhub_cred', url: 'https://index.docker.io/v1/') {
          sh 'docker push chaitanyajoshi27/image918:v2.0'
        }
      }
    }    
  }
}