pipeline {
    agent { node { label 'master' } }
    
     stages {
          

        stage('sonarqube'){

          steps{
            script{ def sonarhome = tool name: 'SQ', type: 'hudson.plugins.sonar.SonarRunnerInstallation';
                    withSonarQubeEnv(credentialsId: 'sonarqub')
                  {
                   sh "${sonarhome}/bin/sonar-scanner "
                  }   
               }
            }
        }
       
  
               
         stage('Deploying Application'){
      
          steps{
                  sh "/var/lib/jenkins/workspace/newdocker.sh"
               }
                post {
                always {
                     cleanWs()
                  }
             //   success {
                    // we only worry about archiving the jar file if the build steps are successful
               //     archiveArtifacts(artifacts: 'target/*.war', allowEmptyArchive: true)
             //   }
            //  failure {
              //    echo "failed"
              // }
           }
        }

       
    }
}
