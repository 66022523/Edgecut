pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server"){
            steps {
                sh "scp -r /var/lib/jenkins/workspace/edgecut/* root@43.208.78.89:~/edgecut"
            }
        }
        
        stage("Build Docker Image") {
            steps {
		ansiblePlaybook playbook: '/var/lib/jenkins/workspace/edgecut/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
		ansiblePlaybook playbook: '/var/lib/jenkins/workspace/edgecut/playbooks/deploy.yaml'
            }    
        } 
    }
}
