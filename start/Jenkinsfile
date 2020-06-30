node {
    stage('Clone') {
        checkout scm
    }
    stage('Update Known Hosts'){
	ansiblePlaybook(
            colorized: true,
            inventory: 'hosts.yml',
            playbook: 'prepare/known_hosts.yml'
	)
    }
    stage('Install') {
        sshagent(['SSH']) {
            ansiblePlaybook (
                become: true, 
                colorized: true, 
                credentialsId: 'SSH', 
                extras: "--extra-vars='public_key=$PUBLIC_KEY'", 
                inventory: 'hosts.yml', 
                playbook: 'prepare/playbook.yml', 
                vaultCredentialsId: 'VAULT',
            )
        }
    }
}
