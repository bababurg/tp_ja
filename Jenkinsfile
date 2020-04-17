pipeline {

        agent {
                docker {
                        image 'node:6-alpine'
                        args '-p 3000:3000'
                }
        }

        environment {
                CI = 'true'
        }


        stages {

            stage('Build') {
                steps {
                    sh 'npm install'
                }
            }

            stage('Test') {
                     steps {
                             sh 'npm test'
                     }
             }

             stage('Install ansible') {
                     steps {
                             script {
                                     sh 'apk add ansible'
                             }

                             script {
                                     sh 'apk add python3'
                             }
                     }
                        
             }

             stage('Launch Ansible') {
                     steps {
                             ansiblePlaybook (
                                     colorized: true,
                                     become: true,
                                     playbook: 'playbook.yml'
                                     
                             )
                        }
                }
             
        }
     
}
