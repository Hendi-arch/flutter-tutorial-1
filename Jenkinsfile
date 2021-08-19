pipeline {
    agent { label 'Flutter x Jenkins' }

    // Application stages
    stages {
        stage('Build') {
            steps {
                sh './jenkins/scripts/flutter-build.sh'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/flutter-test.sh'
            }
        }
        stage('Running') {
            steps {
                sh './jenkins/scripts/flutter-run.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/flutter-kill.sh'
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
