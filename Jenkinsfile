
properties([
   parameters([
      string(defaultValue: 'horsprod', description: 'Quel environnement de deploiement ("prod" ou "horsprod")?', name: 'ENV_FRONT'),
	  string(defaultValue: '', description: 'Votre identifiant ?', name: 'LOGIN'),
	  password(defaultValue: '', description: 'Votre mot de passe ?', name: 'PWD')
   ])
])

node {
	
	stage("Récupération des sources") {
		checkout scm
	}

	stage("Deploiement de l'application Front") {
		sh "echo APPLICATION-FRONT"
	}
	
	if (params.ENV_FRONT == 'prod') {
		stage("Deploiement de l'application Back en prod") {
			sh "echo APPLICATION-BACK"
		}
	}
	echo "La release ${env.BRANCH_NAME} a été déployé sur l'environnement ${params.ENV_FRONT}"
}
