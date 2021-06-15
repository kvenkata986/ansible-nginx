pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                cleanWs()
                // Get some code from a GitHub repository
                sh '''#!/bin/bash
                git clone 'git@github.com:kvenkata986/ansible-nginx.git'
                '''
            }
        }
        stage('Install Nginx') {
            steps {
                sh '''#!/bin/bash
                cd ansible-nginx
                ansible-playbook -i /var/lib/jenkins/inventory nginx.yaml --tags install
                '''
            }
        }    
        stage('Update HTML Page') {
            steps {
                sh '''#!/bin/bash
                cd ansible-nginx
                ansible-playbook -i /var/lib/jenkins/inventory nginx.yaml --tags setup
                '''
            }			
        }
    }
}
