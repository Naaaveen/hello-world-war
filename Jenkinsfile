pipeline {
  agent {label 'master'}
    stages {
      stage ('checkout') {
        steps {
                sh 'rm -rf hello-world-war'
                sh 'git pull https://github.com/Naaaveen/hello-world-war.git'
                sh 'pwd'
                sh 'ls'
        }
      }
      stage ('build') {
        steps {
                sh 'docker build -t sampleimage:latest .'
                
        }
      }
      stage ('publish') {
        steps {
                 sh 'docker login -u naviq007 -p Madhu@12345'
                 sh 'docker tag sampleimage:latest naviq007/cicdrepo:lts'
                 sh 'docker push naviq007/cicdrepo:lts'
        }
      }
      
      stage ('deploy') {
        agent {label 'test'}
        steps {
                 sh 'docker login -u naviq007 -p Madhu@12345'
                 sh 'docker pull naviq007/cicdrepo:lts'
                 sh 'docker rm -rf test'
                 sh 'docker run -d -p 8088:8080 --name test naviq007/cicdrepo:lts'
        }  
      }   
    }
}
                
        
                
