node ('master')
{
    stage('ContinuousDownload-loans')
    {
        git 'https://github.com/krazyahmed/continuous-download.git'
    }
    stage('ContinuousBuild-loans')
    {
        sh label: '', script: 'mvn package'
    }
    stage('ContinuousDeployment-loans')
    {
       sh label: '', script: 'scp /root/.jenkins/workspace/Declarative-git-1/webapp/target/webapp.war root@192.168.225.142:/root/workspace/test200.war'
    }
    stage('ContinuousTesting-loans')
    {
        git 'https://github.com/selenium-saikrishna/TestingNew.git'
    }
    stage('ContinuousDelivery-loans')
    {
        input message: 'waiting for approval from Delivery Team', submitter: 'sai'
        sh label: '', script: 'scp /root/.jenkins/workspace/Declarative-git-1/webapp/target/webapp.war root@192.168.225.142:/root/workspace/test200test.war'
    }
}
