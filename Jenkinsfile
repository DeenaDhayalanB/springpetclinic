env.dockerimagename="devopsbasservice/buildonframework:buildonJenkinsfile2.0"
pipeline
{
  agent any


  stages()
    {
        stage ('Module2-Demo-Build')
                {
				steps
                    {
                        git url:'https://github.com/devopsbasservice/springpetclinic.git'
                        sh 'mvn clean package -DskipTests=true'
                    }
                }
        stage ('Module2-Demo_CodeAnalysis')
				{
                steps 
					{
						sh 'mvn sonar:sonar -Dsonar.host.url=http://54.209.104.148:9001/ -Dsonar.sources=src/main/java'
                    }
                }
               
        stage ('Module2-Demo_UnitTest') 
				{
				steps 
					{
						sh 'mn test'
					}
				}  
        stage ('Module2-Demo_NexusUpload') 
				{
				steps 
					{
						sh 'curl -v -u admin:admin123 --upload-file /var/jenkins/jobs/$commitID/workspace/target/java-maven-junit-helloworld-1.0-SNAPSHOT.jar http://54.209.104.148:8081/nexus/content/repositories/buildonrepo/$commitID.war'
					}
				}

    }
}
