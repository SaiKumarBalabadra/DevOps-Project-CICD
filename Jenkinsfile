pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS_ID = 'docker-creds'
        DOCKER_REPO = 'isaikumarbalabadra/ronin-space'
        SONARQUBE_SERVER = 'http://localhost:9000/'
        SONARQUBE_TOKEN = credentials('sonar-token')
        TRIVY_IMAGE = 'aquasec/trivy:latest'
        APP_NAME = 'my-python-app'
        IMAGE_TAG = "jenkins-app"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Scan') {
            steps {
                script {
                    def scannerHome = tool 'SonarQubeScanner'
                    withSonarQubeEnv('SonarQubeScanner') {
                        sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=${APP_NAME} -Dsonar.sources=./src"
                    }
                }
            }
        }
        stage('OWASP Dependency Check') {
            steps {
                sh '''
                /usr/local/bin/dependency-check \
                    --project ${APP_NAME} \
                    --scan ${WORKSPACE} \
                    --format HTML \
                    --out ${WORKSPACE}/owasp-report
                '''
            }
        }        
        stage('Pytest') {
            steps {
                dir('src') {
                    sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt
                    pytest --junitxml=pytest-report.xml
                    '''
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKER_REPO}:${IMAGE_TAG}", "-f build/Dockerfile .")
                }
            }
        }

        stage('Trivy Scan') {
            steps {
                sh '''
                trivy image --exit-code 1 --severity HIGH,CRITICAL --ignorefile ./.trivyignore ${DOCKER_REPO}:${IMAGE_TAG}
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('', DOCKER_CREDENTIALS_ID) {
                        docker.image("${DOCKER_REPO}:${IMAGE_TAG}").push()
                    }
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'src/pytest-report.xml, owasp-report/*', allowEmptyArchive: true
            cleanWs()
        }
    }
}
