pipeline {
    agent any
    stages {
        stage('vcs') {
            steps {
                git branch: 'develop', 
                    url: 'https://github.com/Mahammad986/nopCommerce.git'    
            }

        }
        stage('package') {
            steps {
                sh 'dotnet restore src/NopCommerce.sln'
                sh 'dotnet build -c Release src/NopCommerce.sln'
                sh 'dotnet publish -c Release src/Presentation/Nop.Web/Nop.Web.csproj -o publish'
                sh 'mkdir publish/bin publish/logs && zip -r nopCommerce.zip publish'
                archive '**/nopCommerce.zip'
            }

        }
    }
}
