pipeline {
        agent any
        tools {
                maven 'maven 3.8.1'
        }
                stages {
                         stage('cleanup workspace') {

                                             steps {
                                                     echo "${WORKSPACE}"
                                                     echo "cleaning.."
                                             }

                         }
                        
                         stage('Code Checkout') {
                                    steps {
                                        checkout([
                                            $class: 'GitSCM', 
                                            branches: [[name: '*/main']], 
                                            userRemoteConfigs: [[url: 'https://github.com/cigbe00/JenkinsRepo.git']]
                                        ])
                                    }
                        }

                         stage('Compile source') {

                                             steps {
                                                     echo 'compiling java code'
                                                     
                                                     script {
                                                             sh 'cd ${WORKSPACE}/com/chukwudi/example'
                                                             sh 'pwd'
                                                             sh 'ls'
                                                             if (params.RELEASE_BUILD == true) {
                                                                     echo "release build is true"
                                                                     sh 'javac ${WORKSPACE}/src/main/java/com/chukwudi/examples/MessageBuilder.java ${WORKSPACE}/src/main/java/com/chukwudi/examples/MagicBuilder.java'
                                                                     sh 'mvn test'
                                                             }
                                                             else {
                                                                     echo "release is false"
                                                                     sh 'javac ${WORKSPACE}/src/main/java/com/chukwudi/examples/MessageBuilder.java'
                                                                     sh 'mvn -Dtest=TestMessageBuild test'
                                                             }
                                                     }
                                                     echo "${RELEASE_BUILD}"
                                            }

                         }

                         stage(' tar and upload') {
                                         steps {
                                                 sh 'pwd'
                                                 //sh 'jar cvf jenkinsscale.jar bin/driver_classes/NumericConversion.class'
                                         }

                         }



                }





}
