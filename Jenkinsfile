env.dockerimagename="buildon/buildon:v2"
node {
   stage ('SP_Clinic_Build') {
    checkout scm
    sh 'mvn clean package -DskipTests=True'
  }
   stage ('SP_Clinic_CodeAnalysis') {
    sh 'sleep 10s'
   }

   stage ('SP_Clinic_NexusUpload') {
    sh 'echo Hello'
   }
}
