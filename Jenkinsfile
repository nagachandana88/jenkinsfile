pipeline {
   //agent {label 'slavejobs'}
    agent any
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven-3.6.3"      
    }
  stages {
     stage('git clone') {
      steps {
       git credentialsId: 'github', url: 'https://github.com/nagachandana88/pro1.git'
                  }
     }
    stage('Build clean') {
        steps {
         sh 'mvn clean'
        }
    }
 stage('Build compile') {
     steps {
         sh 'mvn compile'
        }
    }
  stage('sonarqube codescan'){
     steps{
            sh'mvn sonar:sonar \
            -Dsonar.projectKey=chandana \
            -Dsonar.host.url=http://3.137.219.230:9000 \
            -Dsonar.login=490b4dfe096bf4bac3529415e6f38b0722f27f0c '
          }
   }
 stage('Build test') {
       steps {
           sh 'mvn test'
        }
    }
 stage('Build package') {
        steps {
         sh 'mvn package'
        }
    }
 stage('Build deploy') {
       steps{
           sh 'mvn deploy'
        }
    }
 }
}
