pipeline {
    agent any
    
    tools {nodejs "nodejs"}
    
    stages {
        stage ('Build Node') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/gitvers/simpleNodeJenkinsReady.git']]])
                sh 'npm install'
                sh 'tar czf Node.tar.gz node_modules app.js package.json' 
                
                
            }
            
        }
        stage ('Build Docker Image') {
            steps {
                script{
                    sh 'docker build -t nodeimage .'
                }
            }
        }
    }
}