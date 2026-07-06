pipeline {
    agent any

    stages {
        stage('Upload to S3') {
            steps {
                sh 'aws s3 sync . s3://my-frontend-demo-2026 --delete'
            }
        }

        stage('CloudFront Invalidation') {
            steps {
                sh 'aws cloudfront create-invalidation --distribution-id E1HMI24YBRVV9L --paths "/*"'
            }
        }
    }
}
