node
    {
        stage('Check Out')
        {
            
            checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '5cf9bd12-2632-4100-b781-4847fab4f37c', url: 'https://github.com/99002634/CucumberReport.git']]])
        
            echo "current build number: ${currentBuild.number}"
            echo "previous build number: ${currentBuild.previousBuild.getNumber()}"
        }
        stage('Clean')
        {
           
            sh' mvn clean '
           
        }
        stage('Execuction of Test Suite')
        {
            
            sh 'mvn clean install -P dev '
            
        }
        stage('Cucumber Report')
        {
            
           cucumber failedFeaturesNumber: -1, failedScenariosNumber: -1, failedStepsNumber: -1, fileIncludePattern: '**/*.json', jsonReportDirectory: 'cucumber-report', pendingStepsNumber: -1, reportTitle: 'Cucumber Report', skippedStepsNumber: -1, sortingMethod: 'ALPHABETICAL', undefinedStepsNumber: -1
           
        }
    }
