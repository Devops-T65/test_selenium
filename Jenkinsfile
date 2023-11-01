pipeline {
    agent any
    stages{
        stage('Checkout'){
            steps{
                git branch:'main',credentialsId:'Github-cred',url:'https://github.com/Devops-T65/test_selenium.git'
            }

        }
        stage('Unittest_with_selenium'){
            when{
                expression{
                    BRANCH_NAME ='main'
                }
            }
            steps{
                echo "---------Executing Unit Test Using Selenium-----------"
                sh "pip install -r requirements.txt"
                sh "python -m unittest"
            }
            post{
                success{
                    git branch:"main", credentialsId: "Github-cred" , url: "https://github.com"
                    sh "git merge main"
                }
            }
        }
    }
}