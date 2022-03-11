pipeline {
    agent { docker 'python:3.5.1' }
    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE = 'sqlite'
    }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
        stage('Test') {
            steps{
                echo 'test'
            }
        }
        stage('deploy') {
            steps {
                input 'Does the staging environment look ok?'
                timeout(time:3 ,unit:'MINUTES'){
                    retry(5){
                        echo 'hello world'
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'this will always run'
        }
        success {
            echo 'this will run only if successful'
        }
        failure {
            echo 'this will run only if failed'
        }
        unstable {
            echo 'this will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}