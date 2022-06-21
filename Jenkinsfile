pipeline {
    agent any
    stages {
        //stage('Checkout') {
        //    steps {
        //        checkout scm
        //    }
        //}
        
        stage('Julieops DryRun') {
            steps {
                sh "/opt/julieops/usr/local/julie-ops/bin/julie-ops-cli.sh --clientConfig confluent-kafka.properties --topology descriptor-topics.yaml --dryRun"
            }
        }
        
        stage('Julieops Run') {
            steps {
                sh "/opt/julieops/usr/local/julie-ops/bin/julie-ops-cli.sh --clientConfig confluent-kafka.properties --topology descriptor-topics.yaml"
            }
        }
    }
    post { 
        always { 
            echo 'Successfully applied'
        }
    }
}