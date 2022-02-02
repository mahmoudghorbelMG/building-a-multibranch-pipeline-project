pipeline {
//    agent any
    agent{ node{ label 'docker-agent' } }
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello world!"'
            }
        }
    }
}
