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
                jar cfe hello.jar Hello -C build .
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
