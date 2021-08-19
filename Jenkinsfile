pipeline {
    agent any
    environment {
        DEVELOPER_DIR="/Applications/Xcode.app/Contents/Developer/"  //This is necessary for Fastlane to access iOS Build things.
        PATH = "/Users/xulu/Projects/flutter_sdk/flutter/bin:/Users/xulu/Library/Android/sdk:/Applications/Xcode.app/Contents/Developer"
    }

    // Application stages
    stages {
        stage('Build') {
            steps {
                sh ('./jenkins/scripts/flutter-build.sh')
            }
        }
        stage('Test') {
            steps {
                sh ('./jenkins/scripts/flutter-test.sh')
            }
        }
        stage('Running') {
            steps {
                sh ('./jenkins/scripts/flutter-run.sh')
            }
        }
    }
    
    // When the Pipeline has finished executing, then clean-up project
    post {
        always {
            sh './jenkins/scripts/flutter-clean.sh'
        }
    }
}
