pipeline {
    agent any
    stages {
        stage('---clean---') {
            steps {
                sh "mvn clean"
            }
        }
        stage('--test--') {
            steps {
                sh "mvn test"
            }
        }
        stage('--package--') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('--jar to nexus--') {
            steps {
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'my-app', 
                        classifier: '', 
                        file: 'target/my-app-1.0.0.jar', 
                        type: 'jar']
                ],
                    credentialsId: 'nexus3', 
                    groupId: 'com.mycompany.app', 
                    nexusUrl: '54.145.23.119:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'myapp_release', 
                    version: '1.0.0'
                //sh "mvn package"
            }
        }
    }
}
