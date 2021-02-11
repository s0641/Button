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
					echo '$(email)'
				}
			}	
   
    			stage("upload")
    			{
				steps
				{
					echo 'uploading the application...'
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
