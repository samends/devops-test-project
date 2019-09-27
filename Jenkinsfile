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

	if (env.BRANCH_NAME == 'master') {
		stage('Deploy Prod') {
			sh "ssh ec2-user@ec2-13-59-235-55.us-east-2.compute.amazonaws.com"
			sh "cd ~/devops-test-project/"
			sh "git pull"
			sh "npm run build"
			sh "cd /usr/share/nginx/html"
			sh "cp -rf ~/devops-test-project/build/* html/"
		}
	}

	if (env.BRANCH_NAME != 'master') {
		stage('Deploy Dev') {

		}
	}
}