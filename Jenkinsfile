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
		sh "aws s3 cp ./build s3://deviantwebdev.com --recursive --acl public-read"
	}
}