# Jenkinsfile_pipeline

This project demostrates continuous integration and continuous deployment using Jenkins' pipeline. The pipeline is writted in Jenkinsfile so it can be configured as code.

The job consists of build and deployment.

The job is triggered by (1) polling github repository once a day (written in Jenkinsfile) and (2) new commit to the repository (I haven't figured out how to do it in Jenkinsfile, so the configuration were done in Jenkins gui console and guihut.com -- Jenkins hook url, http://my_jenkins_server/github-webhook/).

The project was implemented in AWS cloud and includes following components:

One Jenkins master running on an aws ec2 ubuntu 16.04 server.
One development Tomcat7 running on an aws ec2 Linux server.
one production Tomcat7 running on an aws ec2 Linux server.


