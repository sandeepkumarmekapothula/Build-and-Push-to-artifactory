pipeline {
    agent any
    tools{
        maven 'maven-3.8.6'
    }

    stages {
        stage('Clone the repository') {
            steps {
               git credentialsId: 'Github_username_password', url: 'https://github.com/sandeepkumarmekapothula/Build-and-Push-to-artifactory.git'
            }
        }
        
    
        stage('Build the code') {
            steps {
            sh 'mvn clean install'
                 }
    }
    
    stage('Deploy to tomcat') {
            steps {
            deploy adapters: [tomcat9(credentialsId: 'tomcat_cred', path: '', url: 'http://50.16.21.157:8081')], contextPath: null, war: '**/*.war'
                 }
    }
}
}
