pipeline {
    agent {
        node {
            label 'built-in' // Use Jenkins' built-in node
        }
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Hello, World!BAby SupppHiiiiiian '
            }
        }
    }
    
     post {
        success {
            script {
                def commitSHA = 'YOUR_SHA'  // You'd typically fetch this dynamically
                def response = httpRequest url: 'https://app.sleuth.io/api/1/deployments/testtoken/final-2/register_deploy',
                                           httpMode: 'POST',
                                           contentType: 'APPLICATION_JSON',
                                           headers: [
                                                [name: 'Authorization', value: 'Bearer YOUR_ACTUAL_ORG_REGISTER_DEPLOY_ACCESS_TOKEN']
                                           ],
                                           validResponseCodes: '100:599',
                                           requestBody: "{\"environment\": \"production\", \"sha\": \"${commitSHA}\"}"

                echo "Response from Sleuth: ${response}"
            }
        }
    }

