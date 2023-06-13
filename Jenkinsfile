pipeline {
    agent any
    environment {
        name = "Gautam"
    }
    parameters {
        string(name : "person", defaultValue : 'Gautam', description : "Who Are You?")
        booleanParam(name : "isMale", defaultValue : "true", description: "Gender")
        choice(name : "City", choices : ['Ajmer', 'Jaipur', 'Mumbai', 'Goa'], description : "")
    }

    stages {
        stage('Run Commands') {
            steps {
                sh '''
                echo "Welcome to DevOps!"
                uname
                pwd
                date
                cal
                ifconfig
                echo "${BUILD_ID}"
                echo "${name}"
                echo "${username}"
                '''
            }
        }
        stage('EnvironmentVariable') {
            environment {
                username = "Abhay"
            }
            steps {
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${name}"'
                sh 'echo "${username}"'
            }
        }
        stage('Parameters') {
            steps {
                sh '''
                echo 'Deploying to test'
                echo "${BUILD_ID}"
                echo "${name}"
                echo "${person}"
                echo "${isMale}"
                echo "${City}"
                '''
            }
        }
        stage('Input Verification') {
            input {
            message 'Should we continue?'
	        ok 'Yes we continue'
            }
            steps {
               sh 'echo "${BUILD_ID}"'
               sh 'echo "${name}"'
               sh 'echo "${username}"'
            }
        }
        stage('HelloWorld-Deploy') {
            steps {
                echo 'Deploying to production'
            }
        }
        stage('HelloWorld-Prod') {
            steps {
                echo 'Deploying to production'
                sh 'echo "${name}"'
                sh 'echo "${username}"'
                sh 'echo "${person}"'
            }
        }

    }
    post {
	always {
		echo "I will always say Hello Again!"
	    }
	failure {
		echo "Failure!"
	    }
	success {
		echo "Success!"
    	}
    }

}
