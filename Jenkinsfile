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
                             sh './src/__tests__/App.test.js'
                     }
             }
             
             stage('Ansible') {
                     steps {
                             ansiblePlaybook (
                                     playbook: 'playbook.yml'
                                     colorized: true,
                                     become: true,
                                     
                             )
                        }
                }
             
        }
     
}
