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

             stage('Install Ansible') {
                     steps {
                             sh 'apt-get install ansible'
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
