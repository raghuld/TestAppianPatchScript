
pipeline {
    agent any

	parameters {
        string(name: 'vcUsername', description: 'Git User Name',defaultValue: 'raghuld')
        string(name: 'vcPassword', description: 'Git Password',defaultValue: 'balaji*98')
        string(name: 'repoUrl', description: 'Git URL',defaultValue: 'https://github.com/raghuld/AppianTest')
        string(name: 'uuid', description: 'Application UUID to generate package',defaultValue: '_a-0000e323-440f-8000-61d0-01ef9001ef90_142549')
		string(name: 'applicationPath', description: 'Path to generate package and import',defaultValue: 'C:\\\\Users\\\\raghuld\\\\Downloads\\\\Stopwatch Timer Component Samples - Update Patch package - 2021-07-15_1606.zip')
		string(name: 'appianURL', description: 'Appian URL ending with suite',defaultValue: 'https://vuramusdemo.appiancloud.com/suite')
		string(name: 'appianUsername', description: 'Appian Username',defaultValue: 'raghuld@vuram.com')
		string(name: 'appianPassword', description: 'Appian Password',defaultValue: 'test124')
		booleanParam(name: 'isFullApplicationImport', description: 'True For Full Appication Import False for patch',defaultValue: 'true')
		string(name: 'startHash', description: 'Considered Only if isFullApplicationImport is false',defaultValue: 'Provide the precedent hash.Only Changes made in the commits after this hash will be considered')
		string(name: 'endHash', description: 'Considered Only if isFullApplicationImport is false.Provide the ending hash to consider',defaultValue: '')


    }
    stages {
        stage('Build') {
            steps {
			script{
			echo 'Building Zip files from Git..'
			bat 'dir'
				dir('C:/Users/raghuld/POC Github Jenkins/Deployment Automation Manager/appian-adm-versioning-client-2.5.12') {
    // some block
			echo "${params.isFullApplicationImport}"
			if("${params.isFullApplicationImport}"=="true" && !"${params.startHash}".isEmpty() && !"${params.endHash}".isEmpty())
			{
				
    	    bat "version-application -vc_username ${params.vcUsername} -vc_password ${params.vcPassword} -repo_url ${params.repoUrl} -action buildSingleApp -uuid ${uuid} -package_path \"${applicationPath}\" -start_hash ${startHash} -end_hash ${endHash}"
				}
			else
			{
				bat "version-application -vc_username ${params.vcUsername} -vc_password ${params.vcPassword} -repo_url ${params.repoUrl} -action buildSingleApp -uuid ${uuid} -package_path \"${applicationPath}\" "
			}
			}
			echo 'Importing Zip files to appian..'
			dir('C:/Users/raghuld/POC Github Jenkins/Deployment Automation Manager/appian-adm-import-client-2.5.12') {
			// Execute Script
				echo "deploy-application -application_path \"${applicationPath}\""
				bat "deploy-application -application_path \"${applicationPath}\" -url ${appianURL} -username ${appianUsername} -password ${appianPassword}"
			}
			}
			
			}
            
        }
      
    }
	post { 
        always { 
            cleanWs()
        }
    }
}
