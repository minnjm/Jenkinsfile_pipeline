pipeline {
    agent any

    parameters {
         string(name: 'tomcat_dev', defaultValue: '34.238.156.123', description: 'Staging Server')
         string(name: 'tomcat_prod', defaultValue: '107.21.139.183', description: 'Production Server')
    }

    triggers {
         pollSCM('* * * * *')
    }

    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deployments'){
            parallel{
                stage ('Deploy to Staging'){
                    steps {
//                        sh "scp -q -i /usr/share/jenkins/tomcat_server_key.pem **/target/*.war ec2-user@${params.tomcat_dev}:/var/lib/tomcat7/webapps"
                        sh "scp -o "UserKnownHostsFile=/dev/null" -o "StrictHostKeyChecking=no" -i /usr/share/jenkins/tomcat_server_key.pem /home/ubuntu/tt ubuntu@34.239.124.201:/home/ubuntu"
                    }
                }

//                stage ("Deploy to Production"){
//                    steps {
//                        sh "scp -q -i /usr/share/jenkins/tomcat_server_key.pem **/target/*.war ec2-user@${params.tomcat_prod}:/var/lib/tomcat7/webapps"
//                    }
//                }
            }
        }
    }
}
