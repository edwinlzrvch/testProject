pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/dotnet/core/sdk:3.1'
        }
    }
    
    stages {
        // stage('Initialize') {
        //     steps {
        //         script {
        //             def dockerHome = tool 'MyDocker'
        //             env.PATH = "${dockerHome}/bin:${env.PATH}"
        //         }
        //     }
        // }
        stage('Git') {
            steps {
                git 'https://github.com/edwinlzrvch/testProject.git'
            }
        }
        stage('Pre-Build') {
             steps {
                // logging tooling versions
                sh 'dotnet --info'
                sh 'dotnet nuget locals all --list'
                sh 'dotnet clean'
            }
        }
        stage('Build') {
            steps {
                sh 'dotnet build'
            }
        }
    }
    post {
        failure {
            mail bcc: '', body: 'Test Fail', cc: '', from: '', replyTo: '', subject: 'Test', to: 'edvins.lazarevichs@binitex.com,  kzitqepuforoiaklbu@ttirv.net'
        }
    }
}