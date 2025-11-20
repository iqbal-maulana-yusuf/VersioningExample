pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Print Message') {
            steps {
                echo "Build triggered from tag!"
            }
        }
    }
}
