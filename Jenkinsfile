@Library('shared_lib_practice') _

pipeline {

    agent any

    stages{

        stage ( 'Git checkout' ) {

            steps{

                script{
                   gitCheckout(
                    branch: "main",
                    url: "https://github.com/Nageshcloud/mrdevops_java_app.git"
                   )

                }
            }
        }
    }

}