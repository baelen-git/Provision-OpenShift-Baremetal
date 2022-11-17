# Description
This repository will hold everything you need to setup the Intersight workflow to provision OpenShift baremetal clusters. 

![Provision OpenShift BM workflow](https://user-images.githubusercontent.com/11138110/201941372-92b1b8af-e611-4b8d-b5f2-acbade6fa00a.jpg)

# Pre requistes
1. An Intersight account
2. 3 or more UCS servers claimed into intersight
3. Intersight premier licenses (90 day trail avaialble)
4. Server Profile Template (example provided)
5. Linux server to host the generated ISO (AWS free tier will suffice, but on-prem is supported through the Intersight Assist.)
6. (optional) create the DNS entries included the PTR records for reverse DNS lookup.

# Steps
1. Create your Policies and Profiles.<br>
Please following the instuctions in [the example directory](examples/README.md) to load the provided example.
2. Import the workflow
3. Login to your Linux server and run the docker container
``` 
docker run -d -p 80:80 baelen/iso-host
```
4. Claim the ISO Host in Intersight as a HTTP target
5. Modify the workflow to use the ISO Host target. <br>
Open the workflow and go to Designer -> Download Discovery ISO.
    1. Go to Inputs and under "External Targets" click on Edit Mapping 
    2. Under External Target click on "Select External Target" and select your ISO_HOST target.
6. Map the Server Worklow Input to the Get Mac Address Task (somehow this doesnt stay mapped during import/export). <br>
Open the workflow and go to Designer -> Get MAC Address.
    1. Go to Inputs and under "Servers" click on Edit Mapping 
    2. Select Direct Mapping -> Workflow Input -> Servers
    3. leave Array Index empty
    
# Validated Setup
UCS C220-M5 Rackmount with 2x M.2 drives
If you modify the Server Profile Template this workflow should support other hardware configurations.


