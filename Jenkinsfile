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
         deploy adapters: [tomcat9(credentialsId: 'd1e7b820-7230-4a51-a80a-60d25db6ba79', path: '', url: 'http://localhost:8989/')], contextPath: null, war: '**/*.war'
       }
       }

     }
}
