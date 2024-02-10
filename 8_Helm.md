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
```

## Templating engine
- Define a common blueprint
- Dynamic values are replaced by placeholders in template file, where values are optained from values.yaml
- Usecase1: In the CI/CD where we replace the files with values.
- Usecase2: Same set of features across multiple environments.
     - Create a chart for the deployment and use the chart for the other environments.


