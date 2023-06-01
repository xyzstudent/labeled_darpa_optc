# labeled_darpa_optc
This code was created for my master thesis. Contact me if you would like to have a copy of it. It is currently under review awaiting grading.
I am a student, so the code and labeling will probably include several mistakes. If you create an issue I will do my best to correct them

I was not able to find a labeled version of the Darpa OPTC dataset, so I did an attempt on my own. 
Contains Code for labeling malicious powershell events in the fiveeyes Darpa OPTC dataset
I did this by converting the ecar data to sysmon ish data, imported into a neo4j database, where I used the ground truth document to label malicious powershell activity.
The parsed data of the subset I selected is about 1 gb compressed. Neo4j database 3 gb compressed. Can provide upon request

To get the ecar data follow the directions here
https://github.com/FiveDirections/OpTC-data




# **Datapreprocessing**
For this thesis only the ecar dataset was used, and of the ecar dataset only a subset of the
data was used, this is due to the sheer size of the dataset.
The subdata that was chosen based on the initial compromise of host based on the
red teams day one and two activities. The host of the initial compromise of those days
were in the folders AIA-201-225 and AIA-501-525 and were collected from the following
ecar folders:
1. 20-23Sep19 (benign data)
2. 23Sep-Night(benign data)
3. 23Sep19-red(mixture of malicous and benign data)
4. 24Sep19(mixture of malicious and benign data)
The data in the different AIA-201-225 and AIA-501-525 folders consists of several compressed json files, which uncompressed each is around 40 gb , except for one last file
which varies from 12-40 gb.
Each of the json files has 11 different object types, with 32 different sub actions. After
doing manual exploration of the object types and sub actions it was determined that the
data in the object type Process with sub action start equals the data of a sysmon event
id 1 process creation. Similarly, the object type FLOW with sub action start has the same
data as sysmon event id 3 Network connection, and object type FILE with sub action
CREATE has the data of sysmon eventid 11 File create. Similarly, the object type Shell
seems to contain the data for the Windows event 800,4103,4104 and 400.
Each of the json files were converted into csv files by using jq. First by using the jq
select function for separating out the different object types process,flow,file and shell
placing them in a temporary json file, then flattening the temporary json files into csv
files as seen in the script function_ecar_to_csv.ipynb in the appendix B.
