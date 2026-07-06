pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/USERNAME/REPOSITORY.git'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy to S3') {
            steps {
                sh 'aws s3 sync build/ s3://YOUR_BUCKET_NAME --delete'
            }
        }

        stage('CloudFront Invalidation') {
            steps {
                sh 'aws cloudfront create-invalidation --distribution-id YOUR_DISTRIBUTION_ID --paths "/*"'
            }
        }

    }
}
