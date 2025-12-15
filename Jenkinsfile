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
               sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@172.31.2.4:/var/lib/tomcat10/webapps/testapp231.war' 
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
                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@172.31.11.41:/var/lib/tomcat10/webapps/prodapp231.war'
            }
        }
    }
}
