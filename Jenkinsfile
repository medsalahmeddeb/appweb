pipeline {
    agent any
    stages {
        stage('Checkout'){
            steps {
                git credentialsId: 'token_github_medsalah', 
                url: 'https://github.com/medsalahmeddeb/appweb'
            }
        }
        stage('Build'){
            tools{
                maven 'Maven3'
                }
            steps{
                sh "mvn clean package"
            }
        }
        stage('Deploy to Tomcat'){
            steps{
                deploy adapters: [
                    tomcat8(credentialsId: 'user_tomcat', 
                        path: '', 
                        url: 'http://10.5.0.23:8090/'
                    )
                    ], 
                    contextPath: null, war: '**/*.war'
            }
        }
    }
}
