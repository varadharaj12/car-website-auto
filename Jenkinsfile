pipeline {
    agent any

    stages {

        stage('Deploy to S3') {
            steps {
                sh 'aws s3 sync . s3://my-frontend-demo-2026 --delete --exclude ".git/*" --exclude "Jenkinsfile"'
            }
        }

        stage('CloudFront Invalidation') {
            steps {
                sh 'aws cloudfront create-invalidation --distribution-id E1HMI24YBRVV9L --paths "/*"'
            }
        }

    }
}
