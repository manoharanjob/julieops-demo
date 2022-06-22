pipeline {
    agent any
    environment { 
        SUCCESS_FLAG = false
    }
    options {
    	skipDefaultCheckout()
    }
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', 
    				branches: [[name: '*/develop']], 
				    doGenerateSubmoduleConfigurations: false, 
				    extensions: [[$class: 'CleanCheckout']], 
				    submoduleCfg: [], 
				    userRemoteConfigs: [[url: 'https://github.com/manoharanjob/julieops-demo']]
				])
            }
        }
        
        stage('Validate') {
            steps {
                sh "/opt/julieops/usr/local/julie-ops/bin/julie-ops-cli.sh --clientConfig confluent-kafka.properties --topology descriptor-topics.yaml --dryRun"
            }
        }
        
        stage('Deploy') {
            steps {
                sh "/opt/julieops/usr/local/julie-ops/bin/julie-ops-cli.sh --clientConfig confluent-kafka.properties --topology descriptor-topics.yaml"
            }
        }
    }
    post {
	    success {
	    	echo 'Success'
	    }
	    failure {
	    	echo 'Failed'
	  	}
    }
}