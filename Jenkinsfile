pipeline {
    agent any
    tools {
        
        jdk 'jdk17'
        maven 'maven3'
    }
    stages {
        stage('clean workspace') {
            steps {
                cleanWs()
            }
        }
        
        stage('Clone') {
            steps {
                echo 'Cloning..'
                checkout scm
            }
        }
        stage('mvn clean') {
            steps {
                sh 'mvn clean'
            }
        }
        stage('mvn package') {
            steps {
                sh 'mvn package'
            }
        }
        stage('mvn install') {
            steps {
                sh 'mvn install'
            }
        }
        stage('deploy'){
            steps {
                sh 'java -jar target/demo-spring-1.0.0-SNAPSHOT.jar --spring.profiles.active=dev' 
            }
        }
    }
}
