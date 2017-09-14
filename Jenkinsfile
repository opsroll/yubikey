pipeline {
    agent any

    stages {
        stage('Lint') {
            steps {
                sh """
                  wget https://bootstrap.pypa.io/get-pip.py
                  python get-pip.py
                  source .envrc
                  ansible-lint -x ANSIBLE0004,ANSIBLE0006,ANSIBLE0008,ANSIBLE0015,ANSIBLE0012,ANSIBLE0011,ANSIBLE0013,ANSIBLE0010
                """
            }
        }
        stage('Test'){
            steps {
                sh 'make check'
                junit 'reports/**/*.xml'
            }
        }
        stage('Package') {
            steps {
                sh 'make publish'
            }
        }
    }
}
