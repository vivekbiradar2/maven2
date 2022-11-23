node('built-in')
{
   stage('ContinuousDownload') 
   {
      git 'https://github.com/intelliqittrainings/maven.git'
   }
   stage('ContinuousBuild')
   {
      sh 'mvn package'
   }
   stage('ContinuousDeployment')
   {
      deploy adapters: [tomcat9(credentialsId: '0f37ad77-1120-420a-8cf3-0e61993da924', path: '', url: 'http://172.31.16.244:8080')], contextPath: 'testapp', war: '**/*.war'
   }
   stage('ContinuousTesting')
   {
      git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
      sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline1/testing.jar'
      
   }
   stage('ContinuousDelivery')
   {
       input message: 'Need approval from DM!', submitter: 'srinivas'
        deploy adapters: [tomcat9(credentialsId: '0f37ad77-1120-420a-8cf3-0e61993da924', path: '', url: 'http://172.31.18.218:8080')], contextPath: 'prodapp', war: '**/*.war'
   }
   
   
   
   
   
   
   
   
   
   
}
