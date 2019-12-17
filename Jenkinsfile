node {
	def app
	stage('Clone repository'){
		checkout scm
	}

	stage('Build image'){
		app = docker.build('tatitati/example-app')
	}

	stage('Run some tests'){
		app.inside {
			sh 'npm test'
		}
	}

	stage('Push image'){
		docker.withRegistry('https://registry.hub.docker.com', 'mydockerhub_credentials'){
			app.push('latest')
		}
	}
}
