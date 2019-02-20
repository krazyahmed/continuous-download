node ('master')
{
    stage('ContinuousDownload-master')
    {
        git 'https://github.com/selenium-saikrishna/maven.git'
    }
    stage('ContinuousBuild')
    {
        sh label: '', script: 'mvn package'
    }
    stage('ContinuousDeployment-master')
    {
       sh label: '', script: 'scp /root/.jenkins/workspace/dev-master-slave/webapp/target/webapp.war root@192.168.225.142:/root/workspace/test200.war'
    }
    stage('ContinuousTesting-master')
    {
        git 'https://github.com/selenium-saikrishna/TestingNew.git'
    }
    stage('ContinuousDelivery-master')
    {
        input message: 'waiting for approval from Delivery Team', submitter: 'sai'
        sh label: '', script: 'scp /root/.jenkins/workspace/dev-master-slave/webapp/target/webapp.war root@192.168.225.142:/root/workspace/test200test.war'
    }
}
