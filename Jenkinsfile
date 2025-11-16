pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                // Get some code from a GitHub repository
                echo 'Hello!'
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
                    def sourceDir='/var/lib/jenkins/workspace/ProductivityTools.Homer'
                    def destinationDir='/srv/jenkins/pt.googlecloudnetworking'
                    //sh "mkdir -p ${destinationDir}"

                    sh "rsync -av --exclude='.git/' ${sourceDir}/ ${destinationDir}"
                }
            }
        }  


    }
}
