pipeline {
    agent any

    stages {

        stage('Compile Java') {
            steps {
                bat '''
                if exist build rmdir /s /q build
                mkdir build
                javac -d build src\\Hello.java
                "C:\\Users\\Gopi Krishna\\AppData\\Local\\Programs\\Eclipse Adoptium\\jdk-17.0.17.10-hotspot\\bin\\jar.exe" cfe hello.jar Hello -C build .
                '''
            }
        }

        stage('Run') {
            steps {
                bat 'java -jar hello.jar'
            }
        }
    }
}
