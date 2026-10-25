pipeline {
    agent any

    triggers {
        pollSCM('H/2 * * * *')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building JACIT Training Portal'

                sh 'test -f index.html'
                sh 'test -f style.css'

                echo 'Build completed'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing website'

                sh 'grep -q "JACIT Training Portal" index.html'
                sh 'grep -q "stylesheet" index.html'

                echo 'All tests passed'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website to Nginx'

                sh 'cp index.html /var/www/html/index.html'
                sh 'cp style.css /var/www/html/style.css'

                echo 'Deployment completed'
            }
        }
    }
}
