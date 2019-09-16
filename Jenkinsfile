node {
	stage('Checkout') {
		checkout scm
	}

	stage('Test') {
		nodejs(nodeJSInstallationName: 'nodejs') {
			sh 'npm ci'
			sh 'npm run test:ci'
		}
	}

	stage('Build') {
		nodejs(nodeJSInstallationName: 'nodejs') {
			sh 'npm run build'
		}
	}


}