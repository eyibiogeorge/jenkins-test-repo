pipeline {    
    agent any    
        stages {        
            stage('Connect To Github') {            
                steps {                    
                    checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'for-github-login', url: 'https://github.com/eyibiogeorge/jenkins-test-repo.git']])
                }
            }
            stage('Build Docker Image') {            
                steps {                                   
                        sh 'sudo docker build -t dockerfile .'
                }
            }
            stage('Run Docker Container') {           
                steps {                                  
                        sh 'sudo docker run -itd -p 8081:80 dockerfile'                
                }
            }
        }
}