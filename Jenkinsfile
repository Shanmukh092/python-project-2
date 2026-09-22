pipeline{
	agent any

	stages{
		stage("Build"){
			steps{
				sh 'python3 App.py'
			}
		}
		stage("merge"){
			steps{
				withCredentials([
usernamePassword(
credentialsId: 'github-pat',
usernameVariable: 'GIT_USER',
passwordVariable: 'GIT_TOKEN'
)
])
{
				sh '''
				git config user.email "shanukh@local"
				git config user.name "Shanmukh"

				git fetch origin main:refs/remotes/origin/main feature:refs/remotes/origin/feature
				git checkout -B main origin/main

				git merge origin/feature --no-edit

				git push https://${GIT_USER}:${GIT_TOKEN}@github.com/Shanmukh092/python-project-2.git main
				'''
			}
}
		}
	}
	
}
