pipeline {
    agent any
    
    stages {
        stage('Read POM') {
            steps {
                script {
                    def pomContent = readFile 'pom.xml'
                    def pom = new XmlSlurper().parseText(pomContent)
                    
                    println "Project Name: ${pom.artifactId.text()}"
                    println "Project Version: ${pom.version.text()}"
                    // You can access other attributes of the POM as needed
                }
            }
        }
        // Other stages of your pipeline
    }
    // Post-build actions, etc.
}
