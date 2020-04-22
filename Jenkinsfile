pipeline {
     agent any
     stages {

	stage('Lint HTML'){
	
	   steps {
	
		sh 'tidy -q -e *.html'

		}

	}	

         stage('Upload to AWS S3') {
		
             steps {
                
		withAWS(region: 'ap-south-1', credentials: 'jenkins-s3-pipeline') {

		 sh 'echo "Uploading to AWS S3" '
			
		    s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file: 'index.html', bucket: 'static-jenkin-pipeline')
           	
		}
             }
         }
     }
}
