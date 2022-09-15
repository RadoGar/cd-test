pipeline {
    agent { 
        docker { 
            image 'node:16.13.1-alpine' 
        } 
    }
    stages {
        stage('build') {
            steps {
                sh 'node --version'
                prismaCloudScanImage ca: '/certs/server/ca.pem', 
                cert: '/certs/client/cert.pem', 
                dockerAddress: 'https://docker:2376', 
                image: 'node:16.13.1-alpine', 
                key: '/certs/client/key.pem', 
                logLevel: 'debug', 
                podmanPath: '', 
                project: '', 
                resultsFile: 'prisma-cloud-scan-results.json', 
                ignoreImageBuildTime:true
            }
        }        
    }
     post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
