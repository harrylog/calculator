pipeline {
     agent any
     
     stages {


 stage("Checkout") {
               steps {
                    git url:'https://github.com/harrylog/calculator',branch:'master'
               }
          }


stage("Check Java") {
            steps {
                sh "java -version"
            }
        }
         
          
     }
}