# Helam
Package manager for kubernetes; To package YAML files and distribute them in private and public repositories.
Helam charts are more like yum/apt repositories in Linux

## 3 Main actions with Helam charts
- Install
- Upgrade
- Delete


## Helam commands
```bash
helam install <charname>
helam install --values=my-values.yaml <chartname> // this will override the the default values{either we can add new values, or overdide new values}
helam install --set verion=2.0.0 //Another method
helam template <chartname>:: get all the templates with values more like precheck
helam lint <chartname>/
helam install <relasename> --debug --dry-run <chartname> // dry run
helam install <releasename> <chartname>
helam list -a // list the helam charts

```


## 3 Main chart Strucutres of Helam
- Chart.yaml ::- Will have the metadata  more like apiversion,name,description,type,
- template/
- values.yaml :: will have the values thats need to replaced in the mainfest files.

## Templating engine
- Define a common blueprint
- Dynamic values are replaced by placeholders in template file, where values are optained from values.yaml
- Usecase1: In the CI/CD where we replace the files with values.
- Usecase2: Same set of features across multiple environments.
     - Create a chart for the deployment and use the chart for the other environments.

## How to upgrade  with Helam
     Step 1: update the Chart.yaml mention the version number
     step 2: Edit the manifest files as per the needs
     step 3: helam upgrade <release-name> <chartname> .
     
## How to Rollback to previous version
     step1: helm rollback <chartname> <version number>

## How to delete <chart> 
     helam delete chartname
