
node('built-in') {
    stage('ContiniousDownload'){
        git 'https://github.com/Subhasis11/NewWeb.git'
    }
    stage('ContiniousBuild'){
        sh 'mvn package'
    }
    stage('ContiniousDeployment'){
       deploy adapters: [tomcat9(credentialsId: 'e3915c00-042d-4da5-af18-e5149a386d24', path: '', url: 'http://172.31.82.1:8080')], contextPath: 'mytestapp', war: '**/*.war'
    }
   
     stage('ContiniousTesting'){
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/mypipe/testing.jar'
       
    }
    stage('ContiniousDelivery'){
        input message: 'Waiting For Approval', submitter: 'Sri'
        deploy adapters: [tomcat9(credentialsId: 'e3915c00-042d-4da5-af18-e5149a386d24', path: '', url: 'http://172.31.95.221:8080')], contextPath: 'myprod', war: '**/*.war'
    }
   
   
   
}
