#!groovy

pipeline {
 agent any
 environment {
  AWS_REGION = 'eu-west-1'
  AWS_ENV = 'csa0'
  AWS_DOM = 'asxtraining.co.uk'
 }
 stages {
  stage('Build') {
   steps {
    sh 'npm i'
   }
  }
  stage('Unit Test') {
   steps {
    sh 'npm test'
   }
  }
  stage('Dev (Deploy)') {
   environment {
    AWS_STAGE = 'dev'
   }
   steps {
     sh 'serverless create_domain'
     sh 'serverless deploy -s dev'
   }
  }
   stage('Test (Deploy)') {
 environment {
  AWS_STAGE = 'test'
 }
 steps {
  sh 'serverless create_domain'
  sh 'serverless deploy -s test'
 }
}
stage('Inspec Test'){
steps {
sh 'inspec exec api-ping/controls/test.rb'
}
}

 }
}
