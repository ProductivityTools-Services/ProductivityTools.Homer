properties([pipelineTriggers([githubPush()])])

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                // Get some code from a GitHub repository
                echo 'Hello!Test'
            }
        }

        stage('Identify User') {
            steps {
                script {
                    echo "Sprawdzanie, jako który użytkownik Jenkins wykonuje komendy..."

                    // Komenda whoami
                    echo "Nazwa użytkownika (whoami):"
                    sh 'whoami'

                    // Komenda id (bardziej szczegółowa)
                    echo "Szczegóły użytkownika (id):"
                    sh 'id'

                    echo "Zakończono identyfikację użytkownika."
                }
            }
        }

        stage('deleteWorkspace') {
            steps {
                deleteDir()
            }
        }

         stage('clone') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main',
                url: 'https://github.com/ProductivityTools-Services/ProductivityTools.Homer.git'
            }
        }

        stage('Copy the page') {
            steps {
                script{
                    def sourceDir='/var/lib/jenkins/workspace/PT.Homer'
                    def destinationDir='/srv/jenkins/pt.homer'
                    //sh "mkdir -p ${destinationDir}"

                    sh "rsync -av --exclude='.git/' ${sourceDir}/ ${destinationDir}"
                }
            }
        }  


    }
}
