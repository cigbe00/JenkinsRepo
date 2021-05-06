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
                                                     script {
                                                             if (params.RELEASE_BUILD == true) {
                                                                     echo "release build is true"
                                                             }
                                                             else {
                                                                     echo "release is false"
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
