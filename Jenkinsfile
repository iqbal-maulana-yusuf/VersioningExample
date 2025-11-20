pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install GitVersion') {
            steps {
                sh 'dotnet tool install --global GitVersion.Tool'
                sh 'export PATH="$PATH:$HOME/.dotnet/tools"'
            }
        }

        stage('Calculate Version') {
            steps {
                sh '''
                    export PATH="$PATH:$HOME/.dotnet/tools"
                    GitVersion > gitversion.json
                '''
                script {
                    def gv = readJSON file: 'gitversion.json'
                    env.PACKAGE_VERSION = gv.NuGetVersionV2
                    echo "Version Detected: ${env.PACKAGE_VERSION}"
                }
            }
        }

        stage('Pack NuGet') {
            steps {
                sh '''
                    dotnet restore
                    dotnet pack -c Release /p:Version=$PACKAGE_VERSION -o ./output
                '''
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'output/*.nupkg', fingerprint: true
            }
        }
    }
}
