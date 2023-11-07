pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from Git...'
                checkout([$class: 'GitSCM', branches: [[name: '*/master']],
			extensions: [],
			userRemoteConfigs: [[url: 'https://github.com/DaliDevops/MyProject.git']]])
            }
        }
stage('Cleaning the project') {
            steps{
                	sh "mvn -B -MyProject clean  "
           }
        }
        stage('Install') {
            steps {
                echo 'Building Angular project...'
                sh 'npm install'
            }
          stage('Build') {
                sh 'npm run build'
          }
          stage('Access') {
                sh 'ng serve --host 192.168.2.55 --port 4200'
            }
        }
}
post {
   success {
     script {
        sh 'echo "Deployment successfull"'
        //Send a notification via email
         }
      }
  }
}
