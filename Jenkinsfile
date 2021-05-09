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

                         stage('Compile source') {

                                             steps {
                                                     echo 'compiling java code'
                                                     
                                                     script {
                                                             sh 'cd ${WORKSPACE}/com/chukwudi/example'
                                                             sh 'pwd'
                                                             sh 'ls'
                                                             if (params.RELEASE_BUILD == true) {
                                                                     echo "release build is true"
                                                                     sh 'javac ${WORKSPACE}/com/chukwudi/example/MagicBuilder.java ${WORKSPACE}/com/chukwudi/example/MessageBuilder.java'
                                                                     sh 'mvn test'
                                                             }
                                                             else {
                                                                     echo "release is false"
                                                                     sh 'javac ${WORKSPACE}/com/chukwudi/example/MagicBuilder.java MessageBuilder.java'
                                                                     sh 'mvn -Dtest=TestMessageBuilder'
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
