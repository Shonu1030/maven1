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
        deploy adapters: [tomcat9(credentialsId: '66119a22-5da4-4c9c-aef8-dd7c2554146f', path: '', url: 'http://172.31.80.185:8080')], contextPath: 'mytestapp', war: '**/*.war'
}
stage('ContinuousTesting') 
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/hanok1/testing.jar'
}
stage('ContinuousDelivery') 
    {
        deploy adapters: [tomcat9(credentialsId: '66119a22-5da4-4c9c-aef8-dd7c2554146f', path: '', url: 'http://172.31.90.162:8080')], contextPath: 'myprodapp', war: '**/*.war'
}
}
