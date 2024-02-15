pipeline{
    agent any

    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts:'/**target/*.war'
                }
            }
        }
        stage('Deploy to Tomcat server'){
            steps{
                deploy adapters: [tomcat7(credentialsId: 'ff5a60df-c693-44de-835d-799c61559e2a', path: '', url: 'http://3.108.221.41:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}