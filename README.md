# Power Platform / Dynamics 365 ALM Fundamentals
Application Life Cycle Management of Dynamics 365 / Power Platform. (Continuous Integration &amp; Continuous Deployment)

Open https://dev.azure.com 

Install Microsoft Power Platform Build Tools for Azure DevOps from Visual Studio MarketPlace  https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.PowerPlatform-BuildTools

# Power Platform Build Tasks:

Solution Name : $(SolutionName)
Note: This will use the input parameter that you specify when running (queuing) the build pipeline.

# Power Platform Export Solution Task

Unmanged Solution Output File: $(Build.ArtifactStagingDirectory)\$(SolutionName).zip

Manged Solution Output File: $(Build.ArtifactStagingDirectory)\$(SolutionName)_managed .zip

# Power Platform Unpack Solution Task
Solution Input File: $(Build.ArtifactStagingDirectory)\$(SolutionName).zip
Target Folder to unpack solution: $(Build.SourcesDirectory)\$(SolutionName)
Type of solution: Unmanaged
