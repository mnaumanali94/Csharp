node {
    stage 'Checkout'
        checkout scm

    stage 'Prepare'
        bat 'nuget restore "Tester.sln"'
        bat 'nuget install NUnit.Runners -Version 3.2.1 -OutputDirectory testrunner'

    stage 'Build'
        bat "MSBuild.exe /p:Configuration=Release \"Tester.sln\""
        stage 'Test'
        bat "testrunner\\NUnit.ConsoleRunner.3.2.1\\tools\\nunit3-console.exe Tester.Tests\\bin\\Release\Tester.Tests.dll"            
     }