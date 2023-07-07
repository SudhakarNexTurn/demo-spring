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
                sh 'version=mvn help:evaluate -Dexpression=project.version -q -DforceStdout'
                sh 'project=mvn help:evaluate -Dexpression=project.name -q -DforceStdout'
                sh 'java -jar target/$project-$version.jar --spring.profiles.active=dev' 
            }
        }
    }
}
