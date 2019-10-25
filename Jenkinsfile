node {
   stage('init') {
      checkout scm
   }
   stage('build') {
      sh '''
         cd complete
         mvn clean package
 
         cp src/main/resources/web.config web.config
        
         zip todo.zip web.config
      '''
   }
   stage('deploy') {
      azureWebAppPublish azureCredentialsId: env.AZURE_CRED_ID,
      resourceGroup: env.RES_GROUP, appName: env.WEB_APP, filePath: "**/todo.zip"
   }
}
