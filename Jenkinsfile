pipeline {

    agent any

    environment {
        LANG = 'en_US.UTF-8'
        LC_ALL = 'en_US.UTF-8'
    }

    // Fix UTF-8 encoding issues

    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout') {
            steps {

                git branch: 'master',
                    url: 'https://github.com/PrathwishShetty03/MavenAnsibleWebApp.git'

            }
        }

        stage('Build') {
            steps {

                sh 'mvn clean package'

            }
        }

        stage('Archive') {
            steps {

                archiveArtifacts artifacts: 'target/*.war', fingerprint: true

            }
        }

        stage('Deploy') {
            steps {

                sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'

            }
        }

    }

}
