pipeline
{
    agent any
    stages
    {
        stage('ContionusDownload')
        {
            steps
                {
                    git 'https://github.com/IntelliqDevops/maven.git'
                }    
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeploy')
        {
            steps
            {
               sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@54.241.69.26:/var/lib/tomcat10/webapps/testapp2.war' 
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('ContinuousDelivery')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@52.53.148.125:/var/lib/tomcat10/webapps/prodapp2.war'
            }
        }
    }
}
