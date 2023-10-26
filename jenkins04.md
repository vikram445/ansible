Assignment 4:
Create a Declarative CI pipeline for java based project that contains various stages like
Code checkout
Run the below stages in parallel
- Code stability.
- Code quality analysis.
- Code coverage analysis.
Generate a report for code quality & analysis.
Publish artifacts.
Send Slack and Email notifications.
The user should have the option to skip various scans in the build execution. Before publishing there should be an approval stage to be set in place to approve or deny the publish and if approved the step should execute and the user should be notified post successful/failed
Repeat the same using Scripted Pipeline.



pipeline {
    agent any
    tools {
        maven 'mvn'
    }

    stages {
        stage('Declarative CI Pipeline') {
            steps {
                echo 'This is Declarative Pipeline'
            }
        }
        stage('Code Checkout') {
            steps {
                echo 'Started Cloning'
                git 'https://github.com/samirkesare/DevOpsCodeDemo.git'
            }
        }
        stage('Parallel Phase') {
            parallel {
                stage('Code Stability') {
                    steps {
                        echo "Testing code stability"
                        sh 'mvn test'
                    }
                }
                stage('Code Quality Analysis') {
                    steps {
                        echo "Check code quality using PMD"
                        sh 'mvn pmd:pmd'
                        publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target/pmd-reports', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
                    }
                }
                stage('Code Coverage Analysis') {
                    steps {
                        echo "Check code coverage analysis using Jacoco"
                        sh 'mvn clean verify'
                        jacoco()
                    }
                }
            }
        }
        stage('Approval') {
            steps {
                input message: 'Do you want to proceed with publishing?', ok: 'Approve'
            }
        }
        stage('Publish Artifacts') {
            steps {
                echo 'Start to publish artifact'
                sh 'mvn package'
            }
        }
    }
    
    post {
        success {
            script {
                emailext body: 'Job Succesfully Done', subject: 'Status of job', to: 'singh.vikra3@gmail.com'
                slackSend channel: 'jenkinstesting', message: 'Job run successfully'
            }
        }
        failure {
            script {
                emailext body: 'Job failed', subject: 'Status of job', to: 'singh.vikra3@gmail.com'
                slackSend channel: 'jenkinstesting', message: 'Job failed'
            }
        }
    }
}



![image](https://github.com/vikram445/ansible/assets/79625874/1d39b91f-343c-49bf-9d9d-68f8a53240c9)


