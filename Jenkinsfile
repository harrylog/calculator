pipeline {
     agent any

     stages {
          stage('Checkout') {
                         steps {
                              git url:'https://github.com/harrylog/calculator', branch:'master'
                         }
          }

          stage('Check Java') {
                    steps {
                         sh 'java -version'
                    }
          }

          stage('Compile') {
               steps {
                    sh './gradlew compileJava'
               }
          }
          stage('Unit test') {
               steps {
                    sh './gradlew test'
               }
          }

          stage('Code coverage') {
               steps {
                    sh './gradlew jacocoTestReport'
                    sh './gradlew jacocoTestCoverageVerification'
               }
          }
     }
     post {
          always {
               archiveArtifacts artifacts: 'build/reports/jacoco/**/*', fingerprint: true
          }
     }
}
