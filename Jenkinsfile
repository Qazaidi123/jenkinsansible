pipeline {
  agent { label "${LABEL_NAME}" }

  stages {
    stage ("code") {
      steps {git url:"https://github.com/Qazaidi123/jenkinsansible.git" , branch: "main"
            }
    }
     stage ("Ansible playbook") {
       steps { ansiblePlaybook ( 
         playbook: "ansible/deploy.yaml" ,
         inventory: "ansible/hosts.ini" ,
         credentialsId: "{SSH_KEY}" )
             }
  }  
}
}
