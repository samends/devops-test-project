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
		sh "aws s3 ./build s3://aws.sammenza.com --recursive --acl public-read"
	}
}