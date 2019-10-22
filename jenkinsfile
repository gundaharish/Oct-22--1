node('master') 
{
   stage('ContinuousDownload')
   {
       git 'https://github.com/intelliqittrainings/maven.git'
   }
   stage('ContinuousBuild')
   {
       sh label: '', script: 'mvn package'
   }
   stage('ContinuousDeployment')
   {
       sh label: '', script: 'scp /var/lib/jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.10.97:/var/lib/tomcat8/webapps/qaapp.war'
   }
   stage('ContinuousTesting')
   {
       git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
       sh label: '', script: 'echo "Testing Passed"'
   }
   stage('ContinousDelivery')
   {
       sh label: '', script: '''scp /var/lib/jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.10.88:/var/lib/tomcat8/webapps/prodapp.war
'''
   }
}
