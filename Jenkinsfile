node('built-in')
    {
        stage('ContinousDownload')
            {
                git 'https://github.com/KOMALIMURTHINTI/mavenNew.git'
            }
        
        stage('ContinousBuild')
            {
              sh 'mvn package'
            }
            
        stage('ContinousDeployment')
            {
              deploy adapters: [tomcat9(credentialsId: 'b4498005-6926-4360-ace6-184bc14a3622', path: '', url: 'http://172.31.26.117:8080')], contextPath: 'testapp', war: '**/*.war'
            } 
            
        stage('ContinousTesting')
            {
              git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
              sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline1/testing.jar'
            }   
            
        stage('ContinousDelivery')
            {
              deploy adapters: [tomcat9(credentialsId: 'b4498005-6926-4360-ace6-184bc14a3622', path: '', url: 'http://172.31.27.117:8080')], contextPath: 'prodapp', war: '**/*.war'
            }    
    
