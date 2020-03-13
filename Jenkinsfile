node {
	stage('Checkout') {
		checkout scm
	}

	stage('Test') {
		nodejs(nodeJSInstallationName: 'nodejs') {
			sh "cat src/App.js"
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
		sh "cat build/static/js/*.chunk.js.map"
		sh "aws s3 cp ./build s3://sammenza.com.com --recursive --acl public-read"
	}
}