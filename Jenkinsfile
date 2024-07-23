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
                    jacoco(
                         execPattern: '**/build/jacoco/*.exec',
                         classPattern: '**/build/classes/java/main',
                         sourcePattern: '**/src/main/java',
                         exclusionPattern: '**/test/**'
                    )
               }
          }
     }

     post {
          always {
               publishHTML(target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'build/reports/jacoco/test/html',
                    reportFiles: 'index.html',
                    reportName: 'JaCoCo Coverage Report'
               ])
          }
     }
}
