node {
	stage('Checkout') {
		checkout scm
	}

	stage('Test') {
		nodejs(nodeJSInstallationName: 'nodejs') {
			sh 'npm ci'
			sh 'npm run test'
		}
	}

		stage('Build') {
		nodejs(nodeJSInstallationName: 'nodejs') {
			sh 'npm run build'
		}
	}

	stage('Deploy Prod') {
		sh "scp -r _build/* ec2-user@ec2-13-59-235-55.us-east-2.compute.amazonaws.com:/usr/share/nginx/html"
		// sh "aws s3 cp ./build s3://deviantwebdev.com --recursive --acl public-read"
	}
}