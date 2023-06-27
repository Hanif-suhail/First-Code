pipeline{
	agent{label 'master'}
	stages{
		stage('Checkout'){
			steps{
				git branch: 'vault', url: 'https://github.com/AnjuMeleth/Media99.git'
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
				ansiblePlaybook credentialsId: 'Ansadmin', installation: 'AnsibleCont', inventory: '/home/ansadmin/My_ansible_NP/hosts', playbook: './app_playbook.yml', vaultCredentialsId: 'VaultID1'
   		}
	}
}
