node {
    stage('Code Checkout') { // for display purposes
     echo 'Checout Code and clone it inside jenkins workspace.'
     git 'https://github.com/itrainavengers/maven_apps.git'
   }
   stage('Build code') {
      echo 'Build the package'
      withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
       sh 'mvn clean compile'
     }
   }
   stage('SonarScan') {
      withSonarQubeEnv(credentialsId: 'ItrainSonar', installationName: 'SonarQube') {
         //withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
             sh 'mvn clean package sonar:sonar' 
             //sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.6.0.1398:sonar'
            //sh ' mvn org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar ' +
             //' -Dsonar.host.url=https://sonarcloud.io ' +
             //' -Dsonar.organization=itrainavengers '+ 
             //' -Dsonar.login=c1f3a8036d378aacc1f6e6e2fc6dcd7de2ebae5d '   
         //}
      }
   }
   stage('Artifacts') {
       echo 'package the project artifacts..'
       withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
       sh 'mvn package'
     }
   
   }
   stage('Deploy to Dev'){
       echo 'Deploy to Dev environment'
   }
   stage('Deploy to Test'){
       echo 'Deploy to Test environment'
   }
   stage('Deploy to Prod'){
       echo 'Deploy to Prod environment'
   }
      
   
}
