@Library('my_shared_lib') _

pipeline{

    agent any

    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
    }

    stages{
         
        stage('Git Checkout'){
                    when { expression {  params.action == 'create' } }
                 steps{
                      script{
                      gitCheckout(
                        branch: "main",
                        url: "https://github.com/Nageshcloud/mrdevops_java_app.git"
                      )
                    }
               }
        }
         stage('Build'){
         
         when { expression {  params.action == 'create' } }

            steps{
               script{
                   
                   mvnBuild()
               }
            }
        }
       
    }
}