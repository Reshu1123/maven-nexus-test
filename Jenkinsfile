pipeline {
    agent any
    tools {
        maven 'maven3.6.3'
    }
    stages {
        stage('Build'){
            steps{
                sh script: 'mvn clean deploy'
            }
        }
        stage('Upload war to nexus'){
            steps{
                 nexusArtifactUploader artifacts: [
                     [
                         artifactId: 'JavaSamples',
                         classifier: '', 
                         file: 'target/JavaSamples-1.0.war', 
                         type: 'war'
                     ]
                         ],
                          credentialsId: 'nexus',
                          groupId: 'com.java.samples', 
                          nexusUrl: 'inmyzb0031.in.dst.ibm.com:8081/', 
                          nexusVersion: 'nexus2', 
                          protocol: 'http', 
                          repository: 'sample-rel', 
                          version: '1.0'
            }
        }
    }
}
