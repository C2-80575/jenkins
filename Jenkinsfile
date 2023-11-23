pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/c2-80575/jenkins.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_5VDml6jpBiBeqbRa5C6GXX9qc3Q | /usr/bin/docker login -u amritesh21 --password-stdin'
            }
        }
        stage ('docker build image'){
            steps {
                sh '/usr/bin/docker build -t amritesh21/mywebsite .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push amritesh21/mywebsite'
            }
        }
        stage ('docker remove service'){
            steps{
                sh '/usr/bin/docker service rm myservice'
            }    
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9090:80 --replicas 5 amritesh21/mywebsite'
            }
        }    
    }
}

