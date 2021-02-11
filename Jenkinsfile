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
					script {
                    				final String url = "http://device.pcloudy.com"
						withCredentials([$(email):$(api)(credentialsId: "jenkins-api-token", variable: "token")]) {
                        			final String response = sh(script: "curl -s -u $token $url", returnStdout: true).trim()
							echo response
                   			       }
				}
			}
    
			stage("test")
			{
				when
				{
					expression
					{
						params.executeTest	
					}
				}
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
