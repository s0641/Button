def status="curl -u \"${params.email}: ${params.api}\" https://device.pcloudy.com/api/access | C:\\Users\\S0641\\Desktop\\jq-win64.exe \".result.token\"" 
def upload="curl -X POST -F \"file=@\\Users\\S0641\\Desktop\\Flight.apk\" -F \"source_type=raw\" -F \"token="${token}"\" -F \"filter=all\" https://device.pcloudy.com/api/upload_file"
pipeline
{
	agent any
	tools
	{
		maven 'Maven'
	}
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
					script
					{
						//get auth token
						def output = bat returnStdout: true, script: "${status}"
						echo "Hello  ${output}"
						def list = output.readLines()
						def token = list[list.size()-1]
						echo "Token= ${token}"
						
						
						//upload application
						def uploadFile = bat returnStdout: true, script: "${upload}"
						echo "Hello  ${uploadFile}"
						def arr = uploadFile.readLines()
						def file = arr[arr.size()-1]
						echo "File= ${file}"
						
					}
					echo 'uploading'
				}
			}
    
			stage("test")
			{
				steps
				{
					echo 'testing the application...'
					bat "mvn -version"
					
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
