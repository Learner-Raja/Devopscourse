
# Automate Web Deployment - Ansible

Implemented apache website through Ansible yml file and automate using Jenkins declarative pipeline which clone the code from GitHub repo and run on EC2 Instances.

## Architecture Overview



![atcgitecturediagram](https://github.com/merajaprasad/Automate-Web-Deployment-Ansible/blob/main/architecture.png)


## Jenkins Pipeline


    pipeline {
        agent { label "Ansible-Master-Server" }
        stages {
            stage ('Checkout') {
                steps {
                    checkout scm
                }
            }

            stage ('Run Ansible') {
                steps {
                    script {
                        sh 'sudo -u ansible ansible-playbook /var/lib/jenkins/workspace/${JOB_NAME}/httpd.yml'
                    }
                }
            }
        }
    }
    
