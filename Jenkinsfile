pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server"){
            steps {
                sh "scp -r /var/lib/jenkins/workspace/ansible-neogym/* root@43.208.119.228:~/ansible-neogym"
            }
        }
        
        stage("Build Docker Image") {
            steps {
		ansiblePlaybook playbook: '/var/lib/jenkins/workspace/ansible-neogym/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
		ansiblePlaybook playbook: '/var/lib/jenkins/workspace/ansible-neogym/playbooks/deploy.yaml'
            }    
        } 
    }
}
