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
   junit 'target/surefire-reports/*.xml'
   jacoco execPattern: 'target/jacoco.exec'
   }
   }
   }

    stage('docker build') {
    steps {
    withDockerRegistry([credentialsId: "mbollina", url: ""]) {
    sh'print env'
    sh 'docker build -t mbollina/numeric-app:""$GIT_COMMIT"" .'
    SH 'docker push mbollina/numeric-app:""$GIT_COMMIT"" '
    }   
    }
   }
    
   
  }

}
