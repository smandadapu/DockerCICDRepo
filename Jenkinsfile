#!/usr/bin/env groovy
pipeline { 
agent any

options {
buildDiscarder(logRotator(numToKeepStr: '5')) 
}

parameters {

string(name: 'branch_name', defaultValue: 'master', description: 'branch name to select dynamically' )
string(name: 'env_name', defaultValue: 'dev', description: 'deployment environment selection' )
string(name: 'git_cred', defaultValue: 'git-token', description: 'jenkins with github authetication')
} 

environment {
GITHUB_MAIN_CODE='https://github.com/smandadapu/Git_jenkins_repo.git'

}

stages {
    stage("code checkout")
	{
     steps{
	     script{
		     dir('main'){
			      // withEnv(["GROOVY_HOME=${tool 'groovy-4'}", "PATH=${tool 'groovy-4'}/bin:${PATH}"])
			   
     codeChekOut("${params.branch_name}","${params.git_cred}","${GITHUB_MAIN_CODE}")
			 
		     }
	     }
}
}
}




}

def codeChekOut(String branch_name, String git_cred, String GITHUB_URL)
{
 git branch: branch_name
 url: GITHUB_URL
 credentialsId: git_cred

}
