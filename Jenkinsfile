
properties([
   parameters([
	string(defaultValue: 'horsprod', description: 'Quel environnement de deploiement ("prod" ou "horsprod")?', name: 'ENV_FRONT'),
	booleanParam(defaultValue: false, description: 'Déploiement auto', name: 'AUTO_PARAM'),
	string(defaultValue: '', description: 'Identifiant compte AD', name: 'LOGIN'),
	password(defaultValue: '', description: 'Password compte AD', name: 'PWD')
   ])
])

node {
	
	tag = readVersionFrom('./package.json')

	echo "${tag}"
	
	sh "echo le login est :${LOGIN} et le mot de passe est ${PWD}. "
	
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

def readVersionFrom2(String packageJsonPath) {
	cat ./package.json | grep 'version' | head -1 | awk -F: '{print $2}' | sed 's/[\",]//g' | tr -d '[[:space:]]'
}

@NonCPS
def readVersionFrom(String packageJsonPath) {
    json.parse(packageJsonPath).version.toString()
}