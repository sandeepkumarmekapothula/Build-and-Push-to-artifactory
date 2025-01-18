pipeline {
    agent any
    tools{
        maven 'maven-3.6.3'
    }

    stages {
        stage('GIT Clone') {
            steps {
            git credentialsId: 'Github_username_password', url: 'https://github.com/sandeepkumarmekapothula/Build-and-Push-to-artifactory.git'
            }
        }

        stage('MAVEN Build') {
            steps {
            sh 'mvn clean install'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
            deploy adapters: [tomcat9(credentialsId: 'tomcat-cred', path: '', url: 'http://35.166.236.112:8081')], contextPath: null, war: '**/*.war'
                 }
        }
    }
}
