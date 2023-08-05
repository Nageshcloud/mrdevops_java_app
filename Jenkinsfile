@Library('my_shared_lib') _

pipeline{

    agent any

    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
        string(name: 'hubusername', description: "specify docker hub username", defaultValue: 'nageshle204')
        string(name: 'appname', description: "specify application name", defaultValue: '')
        string(name: 'imagetag', description: "specify docker image tag", defaultValue: '2023')
        
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
        stage('docker Build'){
         
         when { expression {  params.action == 'create' } }

            steps{
               script{
                   
                dockerBuild("${params.hubusername}", "${params.appname}", "${params.imagetag}")
    
               }
            }
        }
        stage('docker image scan'){
         
         when { expression {  params.action == 'create' } }

            steps{
               script{
                   
                trivyScan("${params.hubusername}", "${params.appname}")
    
               }
            }
        }
         stage('docker push'){
         
         when { expression {  params.action == 'create' } }

            steps{
               script{
                   
                dockerPush("${params.hubusername}", "${params.appname}", "${params.imagetag}")
    
               }
            }
        }
       
    }
}