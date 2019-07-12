node {
   stage('init') {
    checkout scm
	}
	  stage('build') {
	   sh '''
	   mvn clean package -DskipTests
	   rm -rf $CATALINA_HOME/webapp/ROOT
	   cp target/calculator-1.0.war src/main/webapp/ROOT.war 
	   '''
	}
	stage('deploy') {
	azureWebAppPublish azureCredentialsId: env.AZURE_CRED_ID,
	resourceGroup: env.RES_GROUP, appName: env.WEB_APP
	}
}