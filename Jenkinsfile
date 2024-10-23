pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/muthu512/demo1.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'scp target/*.jar ubuntu@your-ec2-instance:/home/ubuntu/app'
                sh 'ssh ubuntu@3.108.217.90 "java -jar /home/ubuntu/app/JavaApplication.jar &"'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline successful.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
