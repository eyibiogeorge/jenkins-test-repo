pipeline {    
    agent any    
        stages {        
            stage('Connect To Github') {            
                steps {                    
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'for-github-login', url: 'https://github.com/eyibiogeorge/jenkins-test-repo.git']])
                }
            }
            stage('Build Docker Image') {            
                steps {                
                    script {                    
                        sh 'docker build -t dockerfile .'
                    }
                }
            }
            stage('Run Docker Container') {           
                steps {                
                    script {                    
                        sh 'docker run -itd -p 8081:80 dockerfile'                
                    }
                }
            }
        }
}