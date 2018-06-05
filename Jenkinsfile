pipeline {
   agent {
      label 'jdk8'
   }

   options {
      buildDiscarder(logRotator(numToKeepStr:'10'))
   }

   stages {
      stage('Masters Tests') {
         when {
            branch 'master'
         }
         steps {
            echo "Run the master tests!"
         }
      }
      stage('Development Tests') {
         when {
            beforeAgent true
            branch 'development'
         }
         steps {
            echo "Run the development tests!"
         }
      }
      stage('Build') {
         steps {
            container('maven8') {
               sh 'mvn clean package'
            }
         }
      }
   }
  
}
