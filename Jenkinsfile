pipeline {
    agent any

    stages {
        stage('Check Java') {
            steps {
                bat 'java -version'
            }
        }

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
