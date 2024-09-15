pipeline {
     agent any
      stages {
        stage('Build') {
           steps {
            echo 'start clean and build package'
              sh mvn clean package'
            echo 'end clean and build package'
           }
           post {
             success {
               echo "Archiving the Artifacts"
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
