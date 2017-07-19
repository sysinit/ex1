pipeline {
    agent { docker 'maven:3.3.3' }
    stages {
        stage(`info`) {
          steps {
            echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
          }
        }
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
            }
        }
#        stage('Sanity check') {
#            steps {
#                input "Does the staging environment look ok?"
#            }
#        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }
    post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
}
