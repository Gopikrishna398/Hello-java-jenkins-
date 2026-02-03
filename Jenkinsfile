pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Code already checked out from Git'
            }
        }

        stage('Compile Java') {
            steps {
                bat '''
                if exist build rmdir /s /q build
                mkdir build
                javac -d build src\\Hello.java
                "C:\\Users\Gopi Krishna\AppData\Local\Programs\Eclipse Adoptium\jdk-17.0.17.10-hotspot\bin\jar.exe" cfe hello.jar Hello -C build .
                '''
            }
        }

        stage('Prepare Package Directory') {
            steps {
                bat '''
                if exist package rmdir /s /q package
                mkdir package
                mkdir package\\bin
                copy hello.jar package\\bin\\
                '''
            }
        }

        stage('Create ZIP Package') {
            steps {
                bat '''
                powershell Compress-Archive -Path package\\* -DestinationPath hello-java-%BUILD_NUMBER%.zip
                '''
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: '*.zip'
        }
    }
}
