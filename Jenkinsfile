pipeline {
    agent any

    tools {
        jdk 'jdk-17'
    }

    stages {
        stage('Compile') {
            steps {
                bat 'javac src\\Hello.java'
            }
        }

        stage('Run') {
            steps {
                bat 'java -cp src Hello'
            }
        }
    }
}
