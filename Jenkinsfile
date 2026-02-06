pipeline {
  agent { label "${LABEL_NAME}" }

  stages {
    stage {"code"}
      steps {git url:" " , branch: "main"
            }
     stage {"Ansible playbook"}
       steps { ansibleplaybook ( playbook: "ansible/deploy.yaml" , inventory: "ansible/hosts.ini" )
             }
  }  
}
