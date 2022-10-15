pipeline{
    agent any
    stages{
        stage('Create Infrastructure for the App') {
            steps {
                echo 'Creating Infrastructure for the App on AWS Cloud by using CF Template'
                sh "aws cloudformation create-stack --stack-name serkan-app --template-body file://cfn-template-to-create-k8s-cluster.yml --region 'us-east-1' --capabilities CAPABILITY_NAMED_IAM" 
            }
        }
    }

        stage('wait the instance') {
            steps {
                script {
                    echo 'Waiting for the instance'
                    id = sh(script: 'aws ec2 describe-instances --filters Name=tag-value,Values=Kube-Master-serkan-app Name=instance-state-name,Values=running --query Reservations[*].Instances[*].[InstanceId] --output text',  returnStdout:true).trim()
                    sh 'aws ec2 wait instance-status-ok --instance-ids $id'
                }
            }
        }


        stage('Deploy App on devopstask Kubernetes Cluster'){
            steps {
                echo 'Deploying App on K8s Cluster'
                // sh " helm upgrade --install devopstask-release helm-chart-0.1.0.tgz "
            }
        }





}
