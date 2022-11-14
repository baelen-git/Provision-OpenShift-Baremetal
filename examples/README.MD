## Pre Requisites
Make sure you have [isctl](https://github.com/cgascoig/isctl) installed and configured.

## Steps
1. Open the policies.yaml and modify any environment specific settings.<br>
Have a good look at the NTP and SMPT settings.

2. Create the Policies
```
isctl apply -f policies.yaml
```

3. Create the Server Profile Template
```
isctl apply -f serverProfileTemplate.yaml
```

That's it! you're all set.

## Clean up
To clean up just rust the `isctl apply` commands but add a `-d` at the end.

