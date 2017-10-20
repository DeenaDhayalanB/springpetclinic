env.dockerimagename="devopsbasservice/buildonframework:deepak"
node {
   stage ('SP_Clinic_Build') {
    checkout scm
    sh 'mvn clean package -DskipTests=True'
  }
   stage ('SP_CodeAnalysis123') {
    sh 'sleep 10s'
   }

   stage ('SP_Clinic_NexusUpload') {
    sh 'echo Hello'
   }
}
