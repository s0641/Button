def status="curl -u \"${params.email}: ${params.api}\" https://device.pcloudy.com/api/access"
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
					
					//def script = '''set status=FALSE 
    					//echo %status%'''   
					//def status="bat(script:'set status=FALSE', returnStdout: true)"
					script
					{
						def output = bat returnStdout: true, script: "${status}"
						echo "Hello  ${output}"
						def String token(${output}) {
							output.split("{")[0]
							echo "token  ${token}"
						}
						//def token = output.split('{')[1]
						//echo "token  ${token}"
					}
					
						
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
