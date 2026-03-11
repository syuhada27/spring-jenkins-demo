pipeline {
    agent any

    environment {
        TOMCAT_WEBAPPS = 'C:\\tomcat10\\webapps'
    }

    stages {
        stage('Checkout Source') {
            steps {
                checkout scm
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                bat "copy target\\springdemo*.war %TOMCAT_WEBAPPS%\\springdemo.war"
            }
        }
    }

    post {
        success {
            echo 'Deployment to Tomcat completed successfully! 🚀'
        }
        failure {
            echo 'Build or Deployment failed. Check the logs! ❌'
        }
    }
}