node('built-in')
{
    stage('Download')
    {
        git 'https://github.com/umarshoaibdev-cloud/maven.git'
    }
    stage('Build')
    {
        sh 'mvn package'
    }
    stage('Deploy')
    {
        sh 'scp /var/lib/jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.11.140:/var/lib/tomcat10/webapps/testapp.war'
    }
    stage('Test')
    {
        git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar'
    }
   stage('Delivery')
    {
        sh 'scp /var/lib/jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.11.220:/var/lib/tomcat10/webapps/prodapp.war'
    }
}
