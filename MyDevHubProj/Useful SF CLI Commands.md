@DEPRECATED 5/31/22

# Salesforce CLI commands

Moved to notion: https://bluvato.notion.site/Useful-SF-CLI-Commands-db3965fd3c224504a6daa3115f285ede

List of useful SF CLI commands

---

Authorizing dev hub org
```
sfdx force:auth:web:login --setdefaultdevhubusername
```

Set dev hub
```
sfdx force:config:set defaultdevhubusername="licenses@cta.com" 
```


Show org aliases
```
sfdx force:alias:list
```

Set default org
```
sfdx force:config:set defaultusername=myScratch
```

Open default org
```
sfdx force:org:open
```

SFDX: Push Source to Default Scratch Org
```
sfdx force:source:push --json --loglevel fatal
```

Pull Source
```
sfdx force:source:pull
```


## Packaging

Trailhead (https://trailhead.salesforce.com/content/learn/modules/unlocked-packages-for-customers/organize-your-metadata)


Get the source code for github
```
git clone https://github.com/dreamhouseapp/dreamhouse-lwc.git
```

Authorize dev hub
```
sfdx force:auth:web:login -d -a DevHub
```

confirm your sfdx-project.json file
```
{
   "packageDirectories": [
      {
         "path": "force-app",
         "default": true
      }
   ],
   "namespace": "",
   "sfdcLoginUrl": "https://login.salesforce.com",
   "sourceApiVersion": "54.0"
}
```

Create the package
```
sfdx force:package:create --name dreamhouse --description "My Package" --packagetype Unlocked --path force-app --nonamespace --targetdevhubusername DevHub

Notes:
--name : package name. An alias you can use for future commands.
--path : directory
--packagetype : unlocked.
```

Alter your package versionName & versionNumber

```
{
   "packageDirectories": [
      {
         "path": "force-app",
         "default": true,
         "package": "dreamhouse",
         "versionName": "ver 0.1",
         "versionNumber": "0.1.0.NEXT"
      }
   ],
   "namespace": "",
   "sfdcLoginUrl": "https://login.salesforce.com",
   "sourceApiVersion": "54.0",
   "packageAliases": {
      "dreamhouse": "0Hoxxx"
   }
}
```

Inspect the project-scratch-def.json file : 
```
{
    "orgName": "Dreamhouse",
    "edition": "Developer",
    "features": ["Walkthroughs", "EnableSetPasswordInApi"],
    "settings": {
        "lightningExperienceSettings": {
            "enableS1DesktopEnabled": true
        },
        "mobileSettings": {
            "enableS1EncryptedStoragePref2": false
        }
    }
}
```

Create a scratch org
```
sfdx force:org:create --definitionfile config/project-scratch-def.json --durationdays 30 --setalias MyScratchOrg -v DevHub
```

Alter your package version:

```
{
   "packageDirectories": [
      {
         "path": "force-app",
         "default": true,
         "package": "dreamhouse",
         "versionName": "Version 1.0",
         "versionNumber": "1.0.0.NEXT"
      }
   ],
   "namespace": "",
   "sfdcLoginUrl": "https://login.salesforce.com",
   "sourceApiVersion": "54.0",
   "packageAliases": {
      "dreamhouse": "0Hoxxx"
   }
}
```

Create a package version
```
sfdx force:package:version:create -p dreamhouse -d force-app -k test1234 --wait 10 -v DevHub
```

Install the package version in your scratch org
```
sfdx force:package:install --wait 10 --publishwait 10 --package dreamhouse@1.0.0-1 -k test1234 -r -u MyScratchOrg 
```

Open to view installed pkg
```
sfdx force:org:open -u MyScratchOrg
```

Release pkg version
```
sfdx force:package:version:promote -p dreamhouse@1.0.0-1 -v DevHub
```

Just how do you untangle the contents of you org into separate projects, and ultimately package directories?
```
> Would you like your development teams to be able to release apps, new features, and customizations independently?
> Can you identify metadata that represents an app?
> Can you organize your metadata into modules for distinct features?
> When you create an unmanaged package for this feature or app, what dependencies are you seeing?
```


### Packaging existing 


retrieve (and then unzip)
```
sfdx force:mdapi:retrieve -r ./mdapipkg -u <username> -k ./package.xml
```

unzipt the package.xml

convert this to the default package directory indicated in the sfdx-project.json file
```
sfdx force:mdapi:convert --rootdir mdapi
```









```

```

