  pipeline {
       agent any 

       stages {
           stage('install'){
             downloadTerraform()
             env.PATH = "${env.PATH}:${env.WORKSPACE}"
    }

           stage('init') {
             steps {
                 sh  'terraform init'
      }
    }

           stage('plan'){
             steps {
                 sh 'terraform plan'
    }
  }
   stage('apply'){
      steps {
         sh 'terraform apply'    
    }
  }
if(pullRequest){
  return
}

}
}

// -----------
// Functions
// -----------


def downloadTerraform(){
  if (!fileExists('terraform')) {
    sh "curl -o  terraform_0.8.7_linux_amd64.zip https://releases.hashicorp.com/terraform/0.8.7/terraform_0.8.7_linux_amd64.zip && unzip -o terraform_0.8.7_linux_amd64.zip && chmod 777 terraform"
  } else {
    println("terraform already downloaded")
  }
}
