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
        sh '''./mvnw sonar:sonar \\
  -Dsonar.projectKey=Petclinic \\
  -Dsonar.host.url=http://13.235.74.247:9000 \\
  -Dsonar.login=sqp_7e2cf752c2488094d4f7c8f6599b13414a05a2dd'''
      }
    }

    stage('Unit Test') {
      steps {
        sh '''./mvnw "-Dtest=**/petclinic/*/*.java" test
'''
      }
    }

    stage('Package') {
      steps {
        sh './mvnw package -DskipTests=true'
      }
    }

    stage('Deploy') {
      steps {
        sh './mvnw spring-boot:run </dev/null &>/dev/null &'
      }
    }

  }
}