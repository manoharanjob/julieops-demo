node('') {
	stage ('checkout'){
		checkout scm
	}
	
	stage('julieops dry run') {
		sh "julie-ops-cli.sh --clientConfig confluent-kafka.properties --topology descriptor-topics.yaml --dryRun"
    }
    
    stage('julieops run') {
		sh "julie-ops-cli.sh --clientConfig confluent-kafka.properties --topology descriptor-topics.yaml"
    }
    
}
