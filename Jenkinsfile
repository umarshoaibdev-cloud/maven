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
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'e5d27584-0c4f-4218-9a43-17d6e8873abe', path: '', url: 'http://172.31.2.4:8080')], contextPath: 'testapp', war: '**/*.war'
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
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'e5d27584-0c4f-4218-9a43-17d6e8873abe', path: '', url: 'http://172.31.11.41:8080')], contextPath: 'myprodapp', war: '**/*.war'
            }
        }
    }
}
