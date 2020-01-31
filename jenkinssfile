@Library('shlib1')_
pipeline{
  agent any
  stages{
  
   stage('Create_Repo')
            {
                steps
                 { 
                    bitbucketconnector()
                    logbitbucket(" is created")
                 }
             post{
                failure{
                 logbitbucket(" is not created")
                }
            }
            }
            stage('Collector')
      {
          steps
          {
              bitbucketcollector()
              logbitbucket("is listed")
          }
          post{
                failure{
                 logbitbucket(" is not listed")
                }
            }
      }
stage("bambooConnector"){
            steps{
       bambooconnector()
       log_bamboo("Executed the pipeline Successfully for this project")
      
        }
        post{
        failure{
        log_bamboo("Not Executed the pipeline Successfully for this project")
        }
        }
        }
       
      
       
        stage("bambooCollector"){
            steps{
       bamboocollector()
        log_bamboo("Plan listed Successfully for this project")
        }
         post{
        failure{
        log_bamboo("not listed the plan for this project")
        }
        }
        }
        stage("NexusConnector"){
            steps{
             
       nexusconector()
              log_nexus("is created successfully")
        }
  post{
    failure{
      log_nexus("is not created")
        }
  }
}
    stage("NexusCollector"){
            steps{
             
       nexuscolector()
               log_nexus("is listed successfully")
        }
  post{
    failure{
      log_nexus("does not exist")
        }
  }
        }
        
        
        
         stage('Jira_create_project')
  {    
    steps
    {
            jira_create_project()
            jira_log_con(" project created")
            }
            post{
                failure{
                 jira_log_con("Project not created")
                }
            }
         
    }
  
  stage('Jira_collect_issue')  
  {
    steps 
    {            
             jira_collect_issue()
            jira_log_col("issue collected")
            }
            post{
                failure{
                 jira_log_col("Issue not collected")
                }
            }
    }
  
        }
        }
