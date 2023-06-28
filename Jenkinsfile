pipeline{
	agent{label 'master'}
	stages{
		stage('Checkout'){
			steps{
				git branch: 'vault', url: 'https://github.com/Hanif-suhail/First-Code.git'
			}
		}
    		stage('Setup'){
      			steps{
				sh 'chmod +x install.sh'
        			sh './install.sh'
      			}
    		}
    		stage('Test'){
      			steps{
				 sh '''#!/bin/bash
				     source myprojectenv/bin/activate	
                		     python -m unittest
				     '''
               			}
   		}
		stage('invoke playbook'){
      			steps{
				ansiblePlaybook credentialsId: 'Ansadmin', disableHostKeyChecking: true, inventory: '/etc/ansible/hosts', installation: 'AnsibleCont', playbook: './app_playbook.yml', vaultCredentialsId: 'VaultID1'               			}
   		}
	}
}