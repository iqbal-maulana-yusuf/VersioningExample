pipeline {
    agent any

    options {
        skipDefaultCheckout(false)
    }

    stages {

        stage('Detect Tag') {
            when { buildingTag() }
            steps {
                echo "Tag detected!"
                echo "GIT_TAG: ${env.GIT_TAG}"
                echo "GIT_BRANCH: ${env.GIT_BRANCH}"
            }
        }

        stage('Restore') {
            when { buildingTag() }
            steps {
                echo 'dotnet restore'
            }
        }
    }
    post {
        always {
            echo "Build completed"
        }
    }
}
