pipeline {
	agent {label 'GOL'}
	stages {
    	stage('Build') {
        	steps {
            	// Get some code from a GitHub repository
            	git 'https://github.com/wakaleo/game-of-life.git'


            	// Run Maven on a Unix agent.
            	sh "mvn clean package"


            	// To run Maven on a Windows agent, use
            	// bat "mvn -Dmaven.test.failure.ignore=true clean package"
        	}


        	post {
            	// If Maven was able to run the tests, even if some of the test
            	// failed, record the test results and archive the jar file.
            	success {
                	junit '**/TEST-*.xml'
                	archiveArtifacts '**/*.jar'
            	}
        	}
    	}
	}
}
