pipeline {
    agent any

    parameters {
            choice( name: 'BranchName', choices:['master', 'feature/insprintautomation'], description: "Select your branch" )
            choice( name: 'TestSetName', choices:['CaseStatus'], description: "Select your Testset Name" )
            string( name: 'TestCaseId', defaultValue: '', description: "Select your Test case id execution")
            choice( name: 'environment', choices:['qa','stage','both'], description: "Select your environment" )
            string( name: 'BuildValue', defaultValue: '', description: "Select your BuildValue for execution")
            choice( name: 'RallyKey', choices:['_JPjJEnemSwWylyEWQF7oPQtVkgRzzUl7oTbTU3s0mg','_BPLg2GcoQwW40teVrFHVCkkrOLJtNENqkI3cbfN1AA'], description: "Select your Rally Key" )
            string( name: 'TestSetID', defaultValue: '', description: "Select your TestSetID id")
            string( name: 'BrowserVersion', defaultValue: '81', description: "Select your Browser Version")
            choice( name: 'TcPriority', choices:['"-admin -sales"','"+Critical,+Important,+Useful"'], description: "Select your execution priority" )
    }
    stages {

        stage('Check out'){
            steps {
                println "git checkoutA"
            }
        }

        stage('Build and Execute parallel')
        {
            parallel
            {
                    stage("windows")
                    {
                        stages
                        {

                            stage("QA")
                            {
                                when {
                                    anyOf{

                                     expression { params.environment == "qa"}
                                     expression { params.environment == "both"}
                                  }
                                }
                                steps
                                {
                                   println "It's doing something on QA"
                                }
                            }
                        }
                    }
                    stage("Linux")
                    {
                        stages
                        {
                            stage("STAGE")
                            {
                            when {
                                anyOf{

                                     expression { params.environment == "stage"}
                                     expression { params.environment == "both"}
                                  }
                            }
                                steps
                                {
                                   println "It's doing something on stage"
                                }
                            }
                        }
                    }
            }
        }
    }
 }
