pipeline {

    agent any

    parameters{


    }
    stages{

        stage ( 'Git checkout' ) {

            steps{

                script{
                   gitCheckout(
                    branch: "main",
                    credentialsId: "github_creds",
                    url: "https://github.com/Nageshcloud/mrdevops_java_app.git"
                   )

                }
            }
        }
    }

}