pipeline {
  agent any
  stages {

   stage('Biuild Artifat-maven') {
    steps {
    sh "mvn clean package -DskipTests=true"
    archive 'target/*.jar'
    }   
   
   }
  }

}
