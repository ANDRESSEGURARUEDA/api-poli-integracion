pipeline {
   agent any

   stages {
       stage('Build') {
           steps {
               // Get some code from a GitHub repository
               git 'https://github.com/ANDRESSEGURARUEDA/api-poli-integracion.git'
               // Run Maven on a Unix agent.
               bat "maven clean test"
               // To run Maven on a Windows agent, use
               // bat "mvn -Dmaven.test.failure.ignore=true clean package"
           }
       }
   }
}