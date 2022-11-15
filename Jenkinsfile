pipeline {
	    agent any
	    stages {
	        stage ("Pull") {
	            steps{
	                script{
	                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
	                    userRemoteConfigs:[[
	                        credentialsId: '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', 
	                           url: 'https://github.com/nourelhoudafdhila/projectcd.git']]])
	                }
	            }
	        }
	        stage('npm install'){
	            steps{
	                script{
	                    sh "npm install --force"
	                }
	            }
	        }
	
	        stage('python test'){
	            steps{
	                script{
	                    sh "python3 --version"
	                }
	            }
	        }
	        stage('Build'){
	            steps{
	                script{ 
	                    sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml -e ansible_become_password=123"
	                }
	            }
	            }
	              stage('docker'){
            steps{
                script{
                    sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml"
                }
            }
        }


 }
	            }
