pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                // Your build steps here
                // For example, Maven build
                sh 'mvn clean package'
            }
        }
        stage('Publish') {
            steps {
                script {
                    // def pomXml = readFile('pom.xml')
                    // def pom = new XmlSlurper().parseText(pomXml)

                    // def groupId = pom.groupId.text()
                    // def artifactId = pom.artifactId.text()
                    // def version = pom.version.text()

                    nexusArtifactUploader(
                        nexusVersion: 'nexus3', // Change to 'nexus2' if you're using Nexus 2
                        protocol: 'http', // or 'https' depending on your Nexus setup
                        nexusUrl: 'http://3.81.170.101:8081', // URL of your Nexus server
                        groupId: com.example,
                        version: 1.0-SNAPSHOT,
                        repository: 'maven-releases', // Repository ID in Nexus
                        credentialsId: 'nexus', // ID of Jenkins credentials containing Nexus username and password/token
                        artifacts: [
                            [artifactId: my-web-app, type: 'jar', classifier: '', file: "target/${artifactId}-${version}.jar"]
                        ]
                    )
                }
            }
        }
    }
}
