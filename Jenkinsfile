pipeline {
     agent any
     tools{
          maven 'maven'
          }
      stages {
        stage('Clean') {
           steps {
            echo 'start clean and build package'
            script {
            try{
              sh 'mvn clean'
              }catch(Exception e){
             echo "Failed: ${e}"
              }
              }
            echo 'end clean and build package'
           }
           post {
             success {
               echo "clean Archiving the Artifacts"

             }
           }
        }
        stage('Compile') {
                   steps {
                    echo 'start compile and build package'
                      sh 'mvn compile'
                    echo 'end compile and build package'
                   }
                   post {
                     success {
                       echo "compile Archiving the Artifacts"

                     }
                   }
                }
        stage('Install') {
                         steps {
                          echo 'start Install and build package'
                            sh 'mvn install'
                          echo 'end Install and build package'
                         }
                         post {
                           success {
                             echo "Install Archiving the Artifacts"
                             archiveArtifacts artifacts: '**/target/*.war'
                           }
                         }
                      }
       stage('Deploy to tomcat Server') {
       steps {
         deploy adapters: [tomcat9(credentialsId: 'd1e7b820-7230-4a51-a80a-60d25db6ba79', path: '', url: 'http://localhost:8989/')], contextPath: null, war: '**/*.war'
       }
       }

     }
}
