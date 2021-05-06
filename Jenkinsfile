pipeline {
        agent any
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
                                                     sh 'pwd'
                                                     sh 'ls'
                                                     script {
                                                             sh 'cd com/chukwudi/example'
                                                             if (params.RELEASE_BUILD == true) {
                                                                     echo "release build is true"
                                                                     sh 'javac MagicBuilder.java MessageBuilder.jav'
                                                                     sh 'mvn test'
                                                             }
                                                             else {
                                                                     echo "release is false"
                                                                     sh 'javac MagicBuilder.java MessageBuilder.jav'
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
