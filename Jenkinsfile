node
{
    def maven = tool name: "Maven-3.8.6"
    stage("Checkout git repsitory")
    {
        git branch: 'development', credentialsId: 'git-credentials', url: 'https://github.com/dileepchoutha/maven-web-application.git'
    }
    stage("Build the project")
    {
        sh "${maven}/bin/mvn clean package"
    }
    stage("Depoly the application into tomcat")
    {
        sshagent(['8dd13122-6699-4c19-9a34-2983ea5a8e6b']) 
        {
          sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.95.149.108:~/apache-tomcat-9.0.68/webapps/"
        }
    }
}
