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
    post
    {
        success
        {
            sh 'scp /var/lib/jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.11.220:/var/lib/tomcat10/webapps/prodapp.war'
        }
        failure
        {
            mail bcc: '', body: 'Continuous Integration is giving a failure msg', cc: '', from: '', replyTo: '', subject: 'CI Failed', to: 'selenium.saikrishna@gmail.com'
        }
    }   
}
