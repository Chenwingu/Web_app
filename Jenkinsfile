node('slave') 
{
    stage('Continuous Download')
                   {
                     git branch: 'feature', credentialsId: 'Github.user', url: 'https://github.com/ngasso/techee.git'
                   }
    stage('Continuous build')
                   {
                    sh 'mvn package'
                   }
    stage('Continuous deployment')
                   {
                    deploy adapters: [tomcat8(credentialsId: 'job1-user', path: '', url: 'http://172.31.20.6:8080')], contextPath: 'qaenv', war: '**/*.war'
                   }
    stage('Continuous testing')
                   {
                    sh 'echo "testing has passed"'
                   }
     stage('Continuous delivery')
                   {
                   input message: 'Waiting for approval from executor', submitter: 'ngasso'
                   deploy adapters: [tomcat8(credentialsId: 'prodtime', path: '', url: 'http://172.31.7.218:8080')], contextPath: 'prodenv', war: '**/*.war'
                   }
}
