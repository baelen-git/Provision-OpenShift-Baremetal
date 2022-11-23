# Description
This repository will hold everything you need to setup the Intersight workflow to provision OpenShift baremetal clusters. 

![Provision OpenShift BM workflow](https://user-images.githubusercontent.com/11138110/201941372-92b1b8af-e611-4b8d-b5f2-acbade6fa00a.jpg)

# Pre-requisites
1. An Intersight account
2. 3 or more UCS servers claimed into intersight
3. Intersight premier licenses (90 day trail avaialble)
4. Server Profile Template (example provided)
5. Linux server to host the generated ISO (AWS free tier will suffice, but on-prem is supported through the Intersight Assist.)
6. (optional) create the DNS entries included the PTR records for reverse DNS lookup.

# Steps
1. Create your Policies and Profiles.<br>
Please following the instuctions in [the example directory](examples/README.MD) to load the provided example.
2. Login to your Linux server and run the docker container
``` 
docker run -d -p 80:80 baelen/iso-host
```
3. Claim the ISO Host in Intersight as a HTTP target.<br>
Under Targets click on Claim
    1. Select the HTTP endpoint and click next
    2. If you require an Intersight Assist to connect to your apache server select it first.
    3. Enter the Name, Hostname for your apache server
    4. Use Port 80
    5. No Authentication is required.
    6. No HTTPS needs to be enabled.
4. Import the workflow. After importing the workflow should show as invalid.
5. Modify the workflow to use the ISO Host target. <br>
Open the workflow and go to General -> Workflow Variables.
    1. Behind ISO_HOST click on Pen icon to edit the variable. 
    2. Under "Default Value" click on "Select Default Value"
    3. Select your ISO_HOST click on select and then save.
    3. Hit Save again. Your workflow should now be valid. 
7. Execute the workflow.
    
# Validated Setup
UCS C220-M5 Rackmount with 2x M.2 drives
If you modify the Server Profile Template this workflow should support other hardware configurations.


