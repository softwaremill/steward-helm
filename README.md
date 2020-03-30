# Helm chart for scala-steward

This is a helm chart for [scala steward](https://github.com/fthomas/scala-steward) - the bot that helps you keep library dependencies and sbt plugins up-to-date.

## Quick start

1. Make a copy of the [values.yaml](helm/steward/values.yaml) file.
1. Add your repos to the `repos` key.
1. Set the credentials in `steward` key.
1. Install this chart:
   ```shell script
    helm install -f custom.yaml steward helm/steward
   ```
   
 ## Details
 
 This chart creates a kubernetes CronJob object which periodically checks repositories from `repos` and if a new version of the dependency or plugin is found - it creates a PR.
 Check the [values file](helm/steward/values.yaml) for details.
 
 ## Credits
 
 Based on an internal tool created by [Kasper Kondzielski](https://github.com/ghostbuster91).
 
 Happy helming!
