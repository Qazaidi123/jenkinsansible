pipeline {
  agent { label "${LABEL_NAME}" }

  environment {
    IMAGE_NAME="myimage"
    IMAGE_TAG="${BUILD_NUMBER}"
    CONTAINER_NAME="myimage-container"
    ANSIBLE_SSH_ID="ubuntusshkey"
  }

  stages {
    stage("checkout") {
      steps {
        checkout scm
            }
    }
     stage("Diploy via Ansible playbook") {
       steps { 
         ansiblePlaybook( 
         playbook:"ansible/deploy.yaml" ,
         inventory:"ansible/hosts.ini" ,
         credentialsId:"${ANSIBLE_SSH_ID}",
         extras:"""
          --extra-vars
  '{"image_name"."${IMAGE_NAME}","image_tag"."${IMAGE_TAG}","container_name"."${CONTAINER_NAME}"}'
          """,
           colorized: true,
           disableHostKeyChecking: true
         )
       }
     }
  }
}

