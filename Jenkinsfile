pipeline {
    agent any
    
    stages {
        stage('Read Pom') {
            steps {
                script {
                    def pomXml = readFile('pom.xml')
                    def pom = new XmlSlurper().parseText(pomXml)
                    def groupId = pom.groupId.text()
                    println "GroupId: ${groupId}"
                }
            }
        }
    }
}
