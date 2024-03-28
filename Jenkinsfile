pipeline {
    agent any

//	tools {
//		jdk 'jdk8'
//	}
//	environment {
//		M2_INSTALL = "/usr/bin/mvn"
//	}

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	checkout scm
	    	}
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
		
        stage('Run Tests') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package as WAR') {
            steps {
                sh 'mvn package'
            }
        }
	    
        stage('Deployment') {
            steps {
                sh 'sshpass -p "staragile" scp target/gamutkart.war staragile@172.31.35.187:/home/staragile/apache-tomcat-9.0.85/webapps
            }
        }
    }
}
