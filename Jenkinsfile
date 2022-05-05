node('master')

{

stage('ContinuousDownload') 
   
	 {
	
    git 'https://github.com/ngasso/techee.git' 
    
	}

stage('Continuousbuild') 
   
	 {

   input message: 'Waiting for approval from executor', submitter: 'ngasso'
   sh label: '', script: 'mvn package'
	}
}

