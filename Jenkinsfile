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

	stage('Deploy Prod') {
		sh -tt "ssh ec2-user@ec2-13-59-235-55.us-east-2.compute.amazonaws.com"
		sh -tt "cd ~/devops-test-project/"
		sh -tt "git pull"
		sh -tt "npm run build"
		sh -tt "cd /usr/share/nginx/html"
		sh -tt "cp -rf ~/devops-test-project/build/* html/"
	}
}