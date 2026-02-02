pipeline {
    agent any

    tools {
        maven 'maven'   // must match Jenkins tool name
    }

    stages {

        stage('Initialize') {
            steps {
                sh '''
                echo "PATH=$PATH"
                echo "M2_HOME=$M2_HOME"
                mvn -v
                '''
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
