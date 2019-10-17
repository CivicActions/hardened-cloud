pipeline {
    agent any
    
    stages {
        stage('Build Image') {
            steps {
            withCredentials([file(credentialsId: 'secretcred', variable: 'sec')]) {
                    sh 'env'
                    sh 'whoami'
                    sh "docker run --env-file=$sec -i -v /var/run/docker.sock:/var/run/docker.sock -v \$(pwd):/packer hashicorp/packer:light build -var-file=/packer/variables.json /packer/packer-rhel7-ami.json"
            }}
        }
    }
}
