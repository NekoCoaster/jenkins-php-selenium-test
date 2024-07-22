pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                withMaven(maven: 'Maven 3.6.3') {
                    sh 'mvn clean compile'
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                withMaven(maven: 'Maven 3.6.3') {
                    sh 'mvn exec:exec@install-composer-dependencies'
                }
            }
        }
        stage('Run PHPUnit Tests') {
            steps {
                withMaven(maven: 'Maven 3.6.3') {
                    sh 'mvn exec:exec@run-phpunit-tests'
                }
            }
        }
        stage('Publish Test Results') {
            steps {
                junit 'test-reports/phpunit.xml'
            }
        }
    }
}
