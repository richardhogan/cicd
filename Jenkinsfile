pipeline {
    agent any 

    stages {
        stage('Plan') { 
            steps { 
                cd iaas/aws-vpc
                terraform plan -o vpc-plan.out' 
            }
        }
        stage('Build') { 
            steps { 
                terraform apply -y > vpc-create.out
            }
        }

        stage('Test'){
            steps {
                ssh -i ~/.ssh/rich.hogan ubuntu@
            }
        }

        stage('Deploy') {
            steps {
                sh 'make publish'
            }
        }
    }
}
