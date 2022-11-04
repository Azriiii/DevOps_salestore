pipeline {
	agent any
	stages{
		stage('Checkout Git'){
            steps{
                echo 'Pulling...';
                git branch: 'main',
                url :'https://github.com/Azriiii/DevOps_salestore';
            }
        }

		stage('MVN CLEAN'){
            steps{
                sh 'mvn clean'
            }
        }

		stage('MVN COMPILE'){
            steps{
                sh 'mvn compile'
            }
    	}
			stage('MVN SONARQUBE'){
            steps{
                sh 'mvn sonar:sonar -Dsonar.login=admin -Dsonar.password=sonar'
            }
        }

		stage('JUNIT/MOCKITO'){
            steps{
            echo 'Tests unitaires'
            sh "mvn test"
            }
        }
		 stage('NEXUS')
        {
            steps{
                echo "nexus"
                 sh ' vn clean deploy -DskipTests'
            }
        }


	}
}