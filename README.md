# labeled_darpa_optc
This code was created for my master thesis. Contact me if you would like to have a copy of it. It is currently under review awaiting grading.
I am a student, so the code and labeling will probably include several mistakes. If you create an issue I will do my best to correct them

I was not able to find a labeled version of the Darpa OPTC dataset, so I did an attempt on my own. 
Contains Code for labeling malicious powershell events in the fiveeyes Darpa OPTC dataset
I did this by converting the ecar data to sysmon ish data, imported into a neo4j database, where I used the ground truth document to label malicious powershell activity.
The parsed data of the subset I selected is about 9 gb. Neo4j database 14 gb. Can provide upon request

To get the ecar data follow the directions here
https://github.com/FiveDirections/OpTC-data
