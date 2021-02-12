def ans=""
pipeline
{
	agent any
	parameters
	{
		string(name: 'email', defaultValue:'')
		string(name: 'api', defaultValue:'')
		booleanParam(name: 'executeTest', defaultValue: true, description: '')
	}
 	stages
		{
    			stage("build")
    			{
				steps
				{
					echo 'building the application...'
				}
			}	
   
    			stage("upload")
    			{
				steps
				{
                                      //bat "curl -u \"${params.email}: ${params.api}\" https://device.pcloudy.com/api/access"
					def GIT_COMMIT_EMAIL = bat (
    					script: 'curl -u \"${params.email}: ${params.api}\" https://device.pcloudy.com/api/access',
    					returnStdout: true
					).trim()
					echo "Git committer email: ${GIT_COMMIT_EMAIL}"
						
				}
			}
    
			stage("test")
			{
				steps
				{
					echo 'testing the application...'
				}
			}
   
			stage("deploy")
    			{
				steps
				{
					echo 'deploying the application...'
				}
			}
 		 } 
}
