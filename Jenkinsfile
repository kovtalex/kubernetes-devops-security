pipeline {
  agent any

  stages {
      stage('Build Artifact - Maven') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar'
            }
        } 
      stage('Unit Tests - JUnit and JaCoCo') {
            steps {
              sh "mvn test"
            }
        }
      stage('Unit tests') {
            steps {
              sh "mvn test"
            }
            post {
              junit 'target/surefire-reports/*.xml'
              jacoco execPattern: 'target/jacoco.exec'
            }          
        }      
    }
}
