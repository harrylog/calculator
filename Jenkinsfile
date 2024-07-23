pipeline {
     agent any
     
     stages {


 stage("Checkout") {
               steps {
                    git url:'https://github.com/harrylog/calculator',branch:'master'
               }
          }


stage("Compile") {
               steps {
                    sh "./gradlew compileJava"
               }
          }


          

         
          
     }
}