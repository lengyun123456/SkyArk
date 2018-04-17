# SkyArk
SkyArk is a cloud security project with two helpful sub-modules - AWStealth and AWStrace.

# The Main Goal:
To help the cloud community in the effort of making cloud environments more secure.  
SkyArk currently focuses on mitigating the new threat of Cloud Shadow Admins, and helps organizations to discover, validate and protect cloud privileged entities.  
Stealthy and undercover cloud admins may reside in every public cloud platform and the tool at this time helps mitigating the risk in AWS.

Share your thoughts and feedback:  
Asaf Hecht ([@Hechtov](https://twitter.com/Hechtov)) and CyberArk Labs

# Background:
SkyArk tool is published as part of our presented research at RSA USA this year - on Cloud Shadow Admins:  
https://www.rsaconference.com/videos/quick-look-sneak-your-way-to-cloud-persistenceshadow-admins-are-here-to-stay
  
The research focuses on the new uprising threat of Cloud Shadow Admins - how attackers can find and abuse non-trivial and so called “limited” permissions to still make it through and escalate their privileges and become full cloud admins.  
  
Furthermore, attackers can easily use those tricky specific permissions to hide stealthy admin entities that will wait for them as an undercover persistence technique. We started researching this threat in AWS following its great popularity and later on, we will continue to other cloud vendors as well.

# Tool Description
SkyArk currently contains two modules:
-	**AWSteatlh**:  
Discovers the most privileged entities in the scanned AWS environments - including AWS Shadow Admins.  
With the AWStealth’s scanning results - organizations will know what users, groups and roles have sensitive and risky permissions.  
Potential attackers are hunting those kind of entities. The defensive teams must make sure these privileged entities are well secured - have strong, rotated and safety stored credentials, have MFA enabled, are monitored carefully and so on.  
Remember that we cannot protect the things we don’t know, and AWStealth will help to discover the most privileged entities - the straight-forward admins and the unique stealthy shadow entities that could also easily escalate privileges and become full admins.
-	**AWStrace**:  
Analyzes AWS CloudTrail Logs - the module provides new valuable insights from CloudTrail logs.  
It especially prioritizes risky sensitive IAM actions that potential attackers might use as part of their malicious actions as AWS Shadow Admins.  
The module analyzes the log files and produces informative csv result file with important details on each executed action in the evaluated environment.  
Security teams can use the results files to investigate sensitive actions, discover the entities that took those actions and reveal additional valuable details on each executed and logged action.  
  
# Quick Start  
Each of the modules has more technical explanations in their dedicated readme files - those files reside inside their module’s sub-folder.
 
Start and import SkyArk:
```
1. Import-Module .\SkyArk.ps1 -force
```
Perform AWStealth scan:
```
2. Scan-AWShadowAdmins -accesskeyid [AccessKeyID] -secretkey [SecretAccessKey] -defaultregion [AWS-region]
```
Perform AWStrace analysis:
```
3. Download-CloudTrailLogFiles -AccessKeyID [AccessKeyID]  -SecretKey [SecretAccessKey] -DefaultRegion [AWS-region] -TrailBucketName [CloutTrail-S3bucket] -BucketKeyPrefix [A-Folder-Prefix-To-The-Trail's-Logs]
4. Analyze-CloudTrailLogFiles
```
