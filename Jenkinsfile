node {
   stage('init') {
    checkout scm
	}
	  stage('build') {
	   sh '''
	   mvn clean package -DskipTests
	   cd target
	   rm -rf $CATALINA_HOME/webapps/ROOT
	   cp calculator-1.0.war ../src/main/webapps/ROOT.war 
	   '''
	}
	stage('deploy') {
	azureWebAppPublish azureCredentialsId: env.AZURE_CRED_ID,
	resourceGroup: env.RES_GROUP, appName: env.WEB_APP
	}
}