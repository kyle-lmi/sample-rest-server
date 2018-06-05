pipeline {
   agent {
      label 'jdk8'
   }

   options {
      buildDiscarder(logRotator(numToKeepStr:'10'))
   }

   stages {
      stage('Build') {
         steps {
            container('maven8') {
               sh 'mvn clean package'
            }
         }
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
}
