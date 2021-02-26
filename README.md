# Power Platform / Dynamics 365 ALM Fundamentals
Application Life Cycle Management of Dynamics 365 / Power Platform. (Continuous Integration &amp; Continuous Deployment)

Open https://dev.azure.com 

Install Microsoft Power Platform Build Tools for Azure DevOps from Visual Studio MarketPlace  https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.PowerPlatform-BuildTools

# PowerShell Script

$date=$(Get-Date -UFormat ' %A %B %d, %Y ')

Write-Host "##vso[task.setvariable variable=CurrentDate]$date"

Write-Host "Set CurrentDate to $date"

# Power Platform Build Tasks:

Solution Name : $(SolutionName)

Note: This will use the input parameter that you specify when running (queuing) the build pipeline.
# Power Platform Export Solution Task

Unmanaged Solution Output File: $(Build.ArtifactStagingDirectory)\$(SolutionName).zip

Managed Solution Output File: $(Build.ArtifactStagingDirectory)\$(SolutionName)_managed.zip

# Power Platform Unpack Solution Task
Solution Input File: $(Build.ArtifactStagingDirectory)\$(SolutionName).zip

Target Folder to unpack solution: $(Build.SourcesDirectory)\$(SolutionName)

Type of solution: Unmanaged

# Command line Script

echo commit all changes

git config user.email "userXXX@wrkdevops.onmicrosoft.com"

git config user.name "Automatic Build"

git checkout master

git add --all

git commit -m "solution init"

echo push code to new repo

git -c http.extraheader="AUTHORIZATION: bearer $(System.AccessToken)" push origin maste

# Power Platform Pack Solution task

Source Folder of Solution to Pack: $(Build.SourcesDirectory) \ $(SolutionName)

Solution Output File: $(Build.ArtifactStagingDirectory) \ $(SolutionName).zip

# Power Platform Import Solution task 

Solution input file: $(Build.ArtifactStagingDirectory)\$(SolutionName).zip

# Power Platform Import Solution Realese task 
Solution input file: $(System.DefaultWorkingDirectory)/Build/drop/$(SolutionName)_managed.zip




