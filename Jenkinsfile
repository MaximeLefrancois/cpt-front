
properties([
   parameters([
      string(name: 'ENV_FRONT', defaultValue: 'horsprod', description: 'Quel environnement de deploiement ("prod" ou "horsprod")?')
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
