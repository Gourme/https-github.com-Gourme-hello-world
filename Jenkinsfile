pipeline {
    agent any
    tools { 
        maven 'MyMaven' 
        
    }

    stages {
        
        stage('pull') {
            steps {
                git credentialsId: 'Git_ID', url: 'https://github.com/Gourme/https-github.com-Gourme-hello-world.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean install package'
            }
        }
        stage('codecheck') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('deploy') {
            steps {
                deploy adapters: [tomcat8(credentialsId: 'Tomcat_ID', path: '', url: 'http://15.207.88.114:8080')], contextPath: 'webapp1', onFailure: false, war: '**/*.war'
            }
        }  
        
    }
}

