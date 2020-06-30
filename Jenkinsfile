node {
    stage('Clone') {
        checkout scm
    }
    stage('Run'){
	ansiblePlaybook(
            colorized: true,
            inventory: 'hosts.yml',
            playbook: 'playbook.yml',
	    vaultCredentialsId: 'VAULT'
	)
    } 
}
