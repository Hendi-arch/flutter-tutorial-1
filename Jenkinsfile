pipeline {
    agent { label 'FlutterXJenkins' }
    // environment {
    //     DEVELOPER_DIR="/Applications/Xcode.app/Contents/Developer/"  //This is necessary for Fastlane to access iOS Build things.
    //     PATH = "/Users/xulu/Projects/flutter_sdk/flutter/bin:/Users/xulu/Library/Android/sdk:/Applications/Xcode.app/Contents/Developer"
    // }

    // Application stages
    stages {
        stage('Build') {
            withEnv(['PATH=/Users/xulu/Projects/flutter_sdk/flutter/bin:/Users/xulu/Library/Android/sdk:/Applications/Xcode.app/Contents/Developer']) {
                /* it hangs and fails later with "process apparently never started" */
                sh ('flutter build apk --debug')
            }
        }
        stage('Test') {
            withEnv(['PATH=/Users/xulu/Projects/flutter_sdk/flutter/bin:/Users/xulu/Library/Android/sdk:/Applications/Xcode.app/Contents/Developer']) {
                /* it hangs and fails later with "process apparently never started" */
                sh ('flutter test')
            }
        }
        stage('Running') {
            withEnv(['PATH=/Users/xulu/Projects/flutter_sdk/flutter/bin:/Users/xulu/Library/Android/sdk:/Applications/Xcode.app/Contents/Developer']) {
                /* it hangs and fails later with "process apparently never started" */
                sh ('flutter run --web-allow-expose-url --web-port=5555')
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
