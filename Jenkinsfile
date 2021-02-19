pipeline {
    agent {
        docker {
            image 'maven:3.6-openjdk-8'
            args '-v $HOME/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/srajput45/hello-spring'
                sh "mvn package"
            }
            post {
                success {
                    archiveArtifacts 'target/hello-spring-0.1.0.jar'
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Running commands to execute Test cases'
            }
        }
        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS'
              }
            }
            steps {
                echo 'Running steps to deploy the jar file to nodes'
            }
        }
    }
}
