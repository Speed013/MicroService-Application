pipeline {
    agent any
   // environment {
       // SCANNER_HOME = tool 'sonar-scanner'

 //  }

    stages {
         //   stage('SonarQube') {
       //      steps {
        //        withSonarQubeEnv('sonar-scanner') {
          //          sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=Microservice_Deployment -Dsonar.ProjectName=Microservice_Deployment -Dsonar.java.binaries=.'''
            //    }
         //   }
       // }

        stage('adservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("src/adservice") {
                            sh "docker build -t speed013/adservice:latest ."
                            sh "docker push speed013/adservice:latest"
                            sh "docker rmi speed013/adservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('cartservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("src/cartservice/src") {
                            sh "docker build -t speed013/cartservice:latest ."
                            sh "docker push speed013/cartservice:latest"
                            sh "docker rmi speed013/cartservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('checkoutservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("src/checkoutservice") {
                            sh "docker build -t speed013/checkoutservice:latest ."
                            sh "docker push speed013/checkoutservice:latest"
                            sh "docker rmi speed013/checkoutservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('currencyservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("src/currencyservice") {
                            sh "docker build -t speed013/currencyservice:latest ."
                            sh "docker push speed013/currencyservice:latest"
                            sh "docker rmi speed013/currencyservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('emailservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("src/emailservice") {
                            sh "docker build -t speed013/emailservice:latest ."
                            sh "docker push speed013/emailservice:latest"
                            sh "docker rmi speed013/emailservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('frontend') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("src/frontend") {
                            sh "docker build -t speed013/frontend:latest ."
                            sh "docker push speed013/frontend:latest"
                            sh "docker rmi speed013/frontend:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('loadgenerator') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("src/loadgenerator") {
                            sh "docker build -t speed013/loadgenerator:latest ."
                            sh "docker push speed013/loadgenerator:latest"
                            sh "docker rmi speed013/loadgenerator:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('paymentservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("src/paymentservice") {
                            sh "docker build -t speed013/paymentservice:latest ."
                            sh "docker push speed013/paymentservice:latest"
                            sh "docker rmi speed013/paymentservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('productcatalogservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("src/productcatalogservice") {
                            sh "docker build -t speed013/productcatalogservice:latest ."
                            sh "docker push speed013/productcatalogservice:latest"
                            sh "docker rmi speed013/productcatalogservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('recommendationservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("src/recommendationservice") {
                            sh "docker build -t speed013/recommendationservice:latest ."
                            sh "docker push speed013/recommendationservice:latest"
                            sh "docker rmi speed013/recommendationservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('shippingservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("src/shippingservice") {
                            sh "docker build -t speed013/shippingservice:latest ."
                            sh "docker push speed013/shippingservice:latest"
                            sh "docker rmi speed013/shippingservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('EKS-Deployment') {
            steps {
                withKubeConfig(
                    caCertificate: '',
                    clusterName: 'myAppp-eks-cluster',
                    contextName: '',
                    credentialsId: 'k8s',
                    namespace: 'webapps',
                    restrictKubeConfigAccess: false,
                    serverUrl: 'https://757BB3F1FD14824E9E85D7FE161817EF.gr7.us-east-1.eks.amazonaws.com'
                ) {
                    sh 'kubectl apply -f deployment-service.yaml'
                    sh 'kubectl get pods'
                    sh 'kubectl get svc'
                }
            }
        }
    }
}
