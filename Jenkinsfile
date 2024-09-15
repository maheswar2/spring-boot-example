pipeline{
     agent any
     tools{
     maven 'maven'
     }
     stages{
        stage('Build'){
           steps{
              bat 'mvn clean package'
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
         deploy adapters: [tomcat9(credentialsId: '6323c3a2-2ca5-4b34-9ceb-b1a2b187f721', path: '', url: 'http://localhost:8989/')], contextPath: null, war: '**/*.war'
       }
       }

     }
}
