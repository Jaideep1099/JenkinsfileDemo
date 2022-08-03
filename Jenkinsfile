pipeline {
    agent any
    stages {
        stage('One') {
                steps {
                        echo 'Hi, this is Dr. Rao from India'
			
                }
        }
	    stage('Two'){
		    
		steps {
			input('Do you want to proceed?')
        }
	    }
        stage('Three') {
                when {
                        not {
                                branch "master"
                        }
                }
                steps {
			echo "Hello"
                        }
        }
        stage('Four') {
                steps {
                        echo 'Hi, this is IBM'
			
                }
        }
    }
}
