pipeline {
    agent any
     parameters {
        string(name: 'vcUsername', description: 'Git User Name')
        string(name: 'vcPassword', description: 'Git Password')
        string(name: 'repoUrl', description: 'Git URL')
        file(name: 'applicationPath', description: 'Application Path Local')

    }
    stages {
        stage('Build') {
            steps {
			script{
			echo 'Building..'
			echo "${params.vcUsername}"
            echo "${params.vcPassword}"
            echo "${params.repoUrl}"
            echo "${params.applicationPath}"


			def scriptFileLocation='C:/Users/raghuld/POC Github Jenkins/Deployment Automation Manager/appian-adm-versioning-client-2.5.12'
			bat 'dir'
			echo " My Script location ${scriptFileLocation}"
			dir('C:/Users/raghuld/POC Github Jenkins/Deployment Automation Manager/appian-adm-versioning-client-2.5.12') {
    // some block
    	bat 'version-application'
}
		
			}
            }
        }
    }
}
