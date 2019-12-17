node {
	def app
	stage('Clone repository'){
		checkout scm
	}

	stage('Build image'){
		app = docker.build('tatitati/example-app')
	}

	stage('Push image'){
		docker.withRegistry('https://registry.hub.docker.com', 'mydockerhub_credentials'){
			app.push('latest')
		}
	}
}
