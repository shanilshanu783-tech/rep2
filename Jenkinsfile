pipeline {
    agent none

    stages {
        stage('build') {
            agent {
                label 'buildnode'
            }
            steps {
                deleteDir()

                sh '''
                    git clone https://github.com/shanilshanu783-tech/rep2.git
                    ls -la
                '''

                stash name: 'webpage', includes: 'rep2/**'
            }
        }

        stage('deploy') {
            agent {
                label 'deploynode'
            }
            steps {
                deleteDir()

                unstash 'webpage'

                sh '''
                    rm -rf /var/www/html/*
                    cp -r rep2/* /var/www/html/
                    ls -la
                '''
            }
        }
    }
}
