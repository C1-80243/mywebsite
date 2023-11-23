pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/C1-80243/mywebsite.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_9ql4QDkQbwel79Dm2YQ1XvDDyiI | /usr/bin/docker login -u gaurav831 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t gaurav831/mywebsite .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push gaurav831/mywebsite'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9090:80 --replicas 5 gaurav831/mywebsite'
            }
        }
    }
}
