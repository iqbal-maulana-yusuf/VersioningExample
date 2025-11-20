pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Test') {
            steps {
                echo "try test"
            }
        }
        
         stage('build') {
            steps {
                echo "try test"
            }
        }

        stage('Print Message') {
            steps {
                echo "Build triggered from tag!"
            }
        }
    }
}
