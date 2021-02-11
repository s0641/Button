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
					   final String url = "https://device.pcloudy.com/api/access"
                    			   final String data = "${email}:${api}"
                                           sh """
						response=curl -u "${email}:${api}" https://device.pcloudy.com/api/access
						echo ${response}
						"""
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
