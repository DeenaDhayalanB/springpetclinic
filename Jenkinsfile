env.dockerimagename="devopsbasservice/buildonframework:buildonJenkinsfile2.0"
pipeline
{
  agent any
   
   
  stages() 
    {
			stage ('Module1-Insights_Build')
			{
				   
			
				steps{
					
						//git url:'http://50.17.36.28/root/insights.git'
						sh 'mvn clean package -DskipTests=true'
				}
					
			}
			
			stage ('Module1-Insights-Codeanalysis')
			{
				steps
				{
					sh 'mn sonar:sonar -Dsonar.host.url=http://54.209.104.148:9001/ -Dmaven.test.failure.ignore=true -DskipTests=true -Dsonar.sources=src/main/java'
				}
			}		
			
			stage ('Module1-Insights-Insight_NexusUpload')
			{
				steps
				{
					sh 'curl -v -u admin:admin123 --upload-file /var/jenkins/jobs/$commitID/workspace/PlatformService/target/PlatformService.war http://54.209.104.148:8081/nexus/content/repositories/buildonrepo/Insights-$commitID.war'
				}
			}


    
		stage ('Module2-Onlinebanking-Build')
			{
			
			steps
				{
					git url:'http://50.17.36.28/root/onlinebanking.git'
				    sh 'mvn clean package -DskipTests=true'
				}
			}	
			stage ('Module2-Onlinebanking-Banking_CodeAnalysis') {
			    steps
				{
                     sh 'mvn sonar:sonar -Dsonar.host.url=http://54.209.104.148:9001/ -Dmaven.test.failure.ignore=true -DskipTests=true -Dsonar.sources=src/main/java'
                }
			}
   stage ('Module2-Onlinebanking-Banking_NexusUpload') {
       steps
				{
    sh 'curl -v -u admin:admin123 --upload-file /var/jenkins/jobs/$commitID/workspace/target/onlinebanking.war http://54.209.104.148:8081/nexus/content/repositories/buildonrepo/OnlineBanking-$commitID.war'
				}
   
   } 

    }  
    
}
