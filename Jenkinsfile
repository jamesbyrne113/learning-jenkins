pipeline {
    agent any
    
    stages {
        stage('Git-Checkout') {
            steps {
                echo "git checkout";
                git 'https://github.com/jamesbyrne113/learning-jenkins';
            }
        }
        
        stage('JUnit Tests') {
            steps {
                echo "Running JUnit tests";
                sh 'mvn test'
            }
        }
        
        stage('Package') {
            steps {
                echo "packaging";
                sh 'java -version'
                sh 'mvn -v';
                sh 'mvn package';
            }
        }
        
        stage ('Deploy') {
            steps {
                echo "Deploying";
                deploy adapters: [tomcat9(credentialsId: '0126f6d7-df1e-4d45-b5be-abc76bb41477', path: '', url: 'http://localhost:8070')], contextPath: 'mvn-web-app', onFailure: false, war: '**/*.war';
            }
        }
    }
}