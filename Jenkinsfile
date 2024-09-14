pipeline{
     agent any
     tools{
     maven 'local_maven'
     }
     stages{
        stage('Build'){
           steps{
              sh 'mvn clean package'
           }
           post{
             success{
               echo "Archiving the Artifacts"
               archiveArtifacts artifacts: '**/target/*.war'
             }
           }
        }
       stage('Deploy to tomcat Server'){
       steps{
         deploy adapters: [tomcat9(credentialsId: '8adde575-b394-42f9-8721-2f4e0cb7548d', path: '', url: 'http://localhost:8585/')], contextPath: null, war: '**/*.war'
       }
       }

     }


}