pipeline {
    agent { label 'FlutterXJenkins' }

    // Application stages
    stages {
        stage('Build') {
            steps {
                sh 'Building the application.........'
                sh 'flutter build apk --release && flutter build appbundle --release'
            }
        }
        stage('Test') {
            steps {
                sh 'Application test running............'
                sh 'flutter test'
            }
        }
        stage('Running') {
            steps {
                sh 'Now, you can test access the app, by accessing http://localhost:5555'
                sh 'flutter run --web-allow-expose-url --web-port=5555'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh 'Finish and stop.......'
                sh 'killall -9 dart'
            }
        }
    }
    
    // When the Pipeline has finished executing, then clean-up project
    post {
        always {
            sh 'Clean up project'
            sh 'flutter clean && flutter pub get'
        }
    }
}
