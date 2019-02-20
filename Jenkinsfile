pipeline
{
	agent any
	stages
	{
		stage('ContinuousDownload-loans')
		{
			steps
				{
					git 'https://github.com/krazyahmed/continuous-download.git'
				}
		}
		stage('ContinuousBuild-loans')
		{
			steps
				{
					sh label: '', script: 'mvn package'
				}
		}
		stage('ContinuousDeployment-loans')
		{
			steps
				{
					sh label: '', script: 'scp /root/.jenkins/workspace/Declarative-git-1/webapp/target/webapp.war root@192.168.225.142:/root/workspace/test200.war'
				}
		}
		stage('ContinuousTesting-loans')
		{
			steps
			{
				git 'https://github.com/selenium-saikrishna/TestingNew.git'
			}
			post
			{
				success
				{
					sh label: '', script: 'scp /root/.jenkins/workspace/Declarative-git-1/webapp/target/webapp.war root@192.168.225.142:/root/workspace/test200test.war'
				}
			failure
				{
					mail bcc: '', body: 'FAILED', cc: '', from: '', replyTo: '', subject: 'Jenkins Job Status', to: 'sai@gmail.com'
				}
			}
		}
		
	}
}