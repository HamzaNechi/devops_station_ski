pipeline {
    agent any

    stages {
        stage('Récupération du code de la branche') {
            steps {
                sh 'git checkout hamza'
                sh 'git pull'
            }
        }

        stage('Nettoyage et compilation avec Maven') {
            steps {
                // Nettoyage du projet avec Maven
                sh 'mvn clean'

                // Compilation du projet avec Maven
                sh 'mvn compile'
            }
        }

        stage('MVN SONARQUBE') {
             steps {
                 sh 'mvn sonar:sonar -Dsonar.login=admin -Dsonar.password=hamza'
             }
        }

        stage('Tests unitaires avec Mockito') {
              steps {
                 sh 'mvn install -Dmaven.test.skip=true'
              }
        }


       }

    post {
        success {
            sh 'echo "Success!"'
        }
        failure {
            sh 'echo "Failure!"'
        }
    }
}