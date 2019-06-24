#!groovy
pipeline {
agent any
environment {
AWS_REGION = 'eu-west-1'
AWS_ENV = 'csa0'
AWS_DOM = 'asxtraining.co.uk'
}
stages {
stage('Build'){
steps {
sh 'npm i'
}
}
stage('Unit Test'){
steps {
sh 'npm test'
}
}
stage('Dev (Deploy)') {
environment {
AWS_STAGE = 'dev'
}
steps {
sh 'serverless deploy -s dev'
}
}
}
}
