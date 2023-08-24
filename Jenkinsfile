pipeline {
      agent any
      tools{
            maven 'maven'
      }

      stages {
            stage('Description') {
                  steps {
                        echo 'This Project is to show how Maven execution steps from'
                        echo 'Declarative Pipeline process'
                  }
            }
            stage('Build') {
                  steps {
                        sh 'mvn -f maven-samples/single-module/pom.xml clean package'
                  }

                  post{
                        success{
                              junit '**/target/*/TEST-*.xml'
                              archiveArtifacts artifacts: '**/*.jar'
                        }
                  }
            }
      }

      post{
            always{
                  emailext body: 'This is a Sample Test notification from Jenkins Job.', subject: 'Test Email Notification from Jenkins Job', to: 'devopsbyabhi@gmail.com'
            }
      }
}