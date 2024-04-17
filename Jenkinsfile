pipeline {
    agent any
    
    stages {
        stage('Read POM') {
            steps {
                script {
                    def pom = readMavenPom file: 'pom.xml'
                    println "Project Name: ${pom.name()}"
                    println "Project Version: ${pom.version()}"
                    // You can access other attributes of the POM as needed
                }
            }
        }
        // Other stages of your pipeline
    }
    // Post-build actions, etc.
}
