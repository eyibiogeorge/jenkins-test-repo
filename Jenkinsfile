pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Hi') {
            steps {
                echo 'Hi everyone!!!'
            }
        }
        stage('test') {
            steps {
                echo 'Jenkins test mode activated'
            }
        }
        stage('checkout snippet'){
            steps {
                checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'for-github-login', url: 'https://github.com/eyibiogeorge/jenkins-test-repo.git']])
                sh 'ls -lrt'
            }
        }
    }
}