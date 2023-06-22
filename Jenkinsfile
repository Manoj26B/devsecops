pipeline {
  agent any
  stages {

   stage('Biuild Artifat-maven') {
    steps {
    sh "mvn clean package -DskipTests=true"
    archive 'target/*.jar'
    }   
   
   }

   stage('Testing') {
    steps {
    sh "mvn test"
    }   
   post {
   always {
   junit: 'target/surefire-reports/*.xml'
   jacoco.execPattern: 'target/jacoco.exec'
   }
   }
   }
   
  }

}
