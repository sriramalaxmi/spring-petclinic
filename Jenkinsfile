pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        sh './mvnw clean compile'
      }
    }

    stage('Static Analysis') {
      steps {
        sh '''mvn clean verify sonar:sonar \\
  -Dsonar.projectKey=Petclinic \\
  -Dsonar.host.url=http://13.235.74.247:9000 \\
  -Dsonar.login=sqp_8aaacba90f20db0c4fb973ce26ef542b7a11cea2'''
      }
    }

  }
}