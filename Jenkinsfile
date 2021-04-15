pipeline{
        agent any
        stages{
            stage('Clone repo'){
                steps{
                    sh "git clone git@gitlab.com:qacdevops/chaperootodo_client.git"
                }
            }
            stage('Install Docker and Docker Compose'){
                steps{
                    sh "curl https://get.docker.com | sudo bash"
                    sh 'sudo curl -L "https://github.com/docker/compose/releases/download/1.29.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
                    sh "sudo chmod +x /usr/local/bin/docker-compose"
                }
            }
            stage('deploy'){
                steps{
                    sh "sudo docker-compose pull && sudo -E DB_PASSWORD=${DB_PASSWORD} docker-compose up -d"
                }
            }
        }
}