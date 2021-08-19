pipeline {
    agent { label 'FlutterXJenkins' }
    environment {
        DEVELOPER_DIR="/Applications/Xcode.app/Contents/Developer/"  //This is necessary for Fastlane to access iOS Build things.
        PATH = "/Users/xulu/Projects/flutter_sdk/flutter/bin:/Users/xulu/Library/Android/sdk:/Applications/Xcode.app/Contents/Developer"
    }

    // Application stages
    stages {
        stage('Build') {
            steps {
                sh 'flutter build apk --release && flutter build appbundle --release'
            }
        }
        stage('Test') {
            steps {
                sh 'flutter test'
            }
        }
        stage('Running') {
            steps {
                sh 'flutter run --web-allow-expose-url --web-port=5555'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh 'killall -9 dart'
            }
        }
    }
    
    // When the Pipeline has finished executing, then clean-up project
    post {
        always {
            sh 'flutter clean && flutter pub get'
        }
    }
}
