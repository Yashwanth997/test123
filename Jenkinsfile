
pipeline {
    stages {
        stage('Independent tasks') {
            parallel {
                stage('stage 1') {
                    steps {
                        sh 'exit 1' // failure
                    }
                }
                stage('stage 2') {
                    steps {
                        echo 'Happens even so stage 1 fails'
                        sh 'exit 0' // success
                    }
                }
            }
            post {  // 'stage 3'
                failure {
                    echo "... at least one failed"
                }
                success {
                    echo "Success!"
                }
            }
        }
        stage ('stage 4') {
            steps {
                echo 'Happens only if all previous succeed'
            }
        }
    }
}
