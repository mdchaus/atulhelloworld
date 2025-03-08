pipeline {
    agent any

    //tools {
      //  maven 'Maven 3.9.5' // Ensure this version is configured in Jenkins
      //  jdk 'JDK 17'      // Ensure this JDK version is configured in Jenkins
    //}
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from SCM
                checkout scm
                //javac src/main/java/com/mycompany/app/App.java
                //src/test/java/com/mycompany/app/AppTest.java

            }
        }

        stage('Build') {
            steps {
                // Build the project using Maven
                 //sh 'echo hello'
                //sh 'mvn clean test'

                sh 'mvn -B -DskipTests clean package'
            }
        }

        stage('Test') {
            steps {
                // Run unit tests
                 sh 'echo mvn test'
            }
        }

        stage('Package') {
            steps {
                // Package the application
                sh 'echo mvn package'
            }
        }
        
        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                // Simple deployment example
                sh 'echo "Deploying application..."'
                // Example of copying artifacts to a deploy location
                //java - jar "target/basic-java-app-1.0-SNAPSHOT.jar" 
                
                sh 'ls -l target/'  // Debugging: List JAR files in target/
                //sh 'chmod +x target/*.jar'  // Make JAR executable
                //sh 'java -jar target/basic-java-app-1.0-SNAPSHOT.jar'  // Run JAR file

                //sh 'cp target/basic-java-app-1.0-SNAPSHOT.jar cd /var/lib/jenkins/workspace/HelloWorld_Time_Pipeline/target/'
                sh 'chmod +x jenkins/scripts/deliver.sh'
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }

    post {
        always {
            // Clean up actions
            sh 'echo "Cleaning up..."'
        }

        success {
            // Actions on successful build
            echo 'Build succeeded!'
        }

        failure {
            // Actions on failed build
            echo 'Build failed!'
        }
    }
}
