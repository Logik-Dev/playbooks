node {
    stage('Clone') {
        checkout scm
    }
    stage('Run'){
	sshagent(['SSH']) {
	  ansiblePlaybook(
            credentialsId: 'SSH',
            colorized: true,
            inventory: 'hosts.yml',
            playbook: 'playbook.yml',
	    vaultCredentialsId: 'VAULT'
	)
    }
  }
}
