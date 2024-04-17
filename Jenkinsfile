pipeline {
    agent any
    
    environment {
        NEXUS_URL = 'http://18.209.102.126:8081' // Replace with your Nexus URL
        NEXUS_CREDENTIAL_ID = 'nexus' // Add your Nexus credential ID
    }

    stages {
        stage('Build') {
            steps {
                // You can perform any build steps here, like compiling code, running tests, etc.
                // For example, if you're using Maven:
                sh 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    def pom = readMavenPom file: 'pom.xml' // Read pom.xml file
                    
                    // Extract artifact details from pom.xml
                    def groupId = pom.getGroupId()
                    def artifactId = pom.getArtifactId()
                    def version = pom.getVersion()
                    def packaging = pom.getPackaging()
                    // Use Nexus Platform Plugin to upload artifacts
                    nexusArtifactUploader(
                        nexusVersion: 'nexus3',
                        protocol: 'http',
                        nexusUrl: env.NEXUS_URL,
                        groupId: pom.GroupId,
                        version: pom.Version, // Specify your artifact version
                        repository: 'maven-releases', // Specify your Nexus repository ID
                        credentialsId: env.NEXUS_CREDENTIAL_ID,
                        artifacts: [
                            [artifactId: artifactId, file: "target/${artifactId}-${version}.${packaging}"] // Path to your artifact
                            // You can add more artifacts if needed
                        ]
                    )
                }
            }
        }
    }
}
