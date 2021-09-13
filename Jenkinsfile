#!/usr/bin/env groovy
pipeline { 
agent any

options {
buildDiscarder(logRotator(numToKeepStr: '5')) 
}

parameters {

string(name: 'branch_name', defaultValue: 'master', description: 'branch name to select dynamically' )
string(name: 'env_name', defaultValue: 'dev', description: 'deployment environment selection' )
} 

environment {
git_sourcecode_repo='https://github.com/smandadapu/DockerCICDRepo.git'

}

stages {
    stage("code checkout")
	{
     steps{
     codeChekout("${params.branch_name}")
}
}
}




}

def codeChekout(String branch_name, String git_sourcecode_repo)
{
 git branch: branch_name
 credentialsId: git_cred

}