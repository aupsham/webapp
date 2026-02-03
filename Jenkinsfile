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
        stage('Deploy-To-Nginx') {
    steps {
        sshagent(['nginx']) {
            sh '''
              scp -o StrictHostKeyChecking=no -r \
              dist/* root@172.17.0.2:/usr/share/nginx/html
            '''
            }
          }
        }
            
    }
}
