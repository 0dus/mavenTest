pipeline{
    agent any
    stages{
        stage("Checkout"){
            steps{
                git url: 'https://github.com/0dus/mavenTest.git',branch: 'main'
            }
        }
        stage("Build"){
            steps{
                sh 'mvn clean package'
            }
        }
        stage("Test"){
            steps{
                sh 'mvn test'
            }
        }
    }
    post{
        always{
            junit '**/target/surefire-reports/*.xml'
        }
        success{
            echo 'Build and Tests Successful'
        }
        failure{
            echo 'Build or Test(s) Failed'
        }
    }
}