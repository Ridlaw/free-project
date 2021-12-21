pipeline {
    agent any

    stages {
        stage('Git checkout') {
            steps {
                git 'https://github.com/Ridlaw/free-project.git'
            }
        }
        stage('Build') {
            steps {
                sh ''' cd MywebApp && mvn clean package'''
            }
        }
        stage('Test') {
            steps {
                sh ' cd MywebApp && mvn test'
            }
        }
        stage('deploy to tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'a4aa03c4-6710-47bd-8653-3f8f68ea38c6', path: '', url: 'http://3.16.22.43:8080/')], contextPath: 'webapp', war: '**/*.war'
            }
        }
    }
}
