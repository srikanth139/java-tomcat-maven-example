pipeline {
    agent any

    stages {
        //git stage
        stage('SCM Checkout') {
            steps {
                //echo 'Hello World'
                git credentialsId: 'gitlogindetails', url: 'https://github.com/HARIDARUKUMALLI/java-tomcat-maven-example.git'
            }
        }
        // build stage
        stage('Build stage') {
            steps {
               bat 'mvn clean install sonar:sonar'
            }
        }
    }
}
