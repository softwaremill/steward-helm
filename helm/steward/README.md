# steward

![Version: 0.1.9](https://img.shields.io/badge/Version-0.1.9-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.0](https://img.shields.io/badge/AppVersion-1.0-informational?style=flat-square)

The helm chart for scala steward - the bot that helps you keep library dependencies and sbt plugins up-to-date.

**Homepage:** <https://github.com/fthomas/scala-steward>

## Quick start

1. Make a copy of the values.yaml file.
1. Add your repos to the `repos` key.
1. Set the credentials in `steward` key.
1. Install this chart:
    1. Add the chart repository:
        ```shell script
        helm repo add softwaremill https://charts.softwaremill.com/
        helm repo update
        ```
    1. Install the chart
        ```
        helm install -f custom.yaml <relase-name> softwaremill/steward
        ```
  
## Configuration

The following table lists the configurable parameters of the chart and the default values.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| args | list | `["--workspace","/opt/scala-steward/workspace","--repos-file","/opt/config_values/repos.md","--git-author-name","$(GIT_AUTHOR_NAME)","--git-author-email","$(GIT_AUTHOR_EMAIL)","--vcs-api-host","https://api.github.com","--vcs-login","$(VCS_LOGIN)","--git-ask-pass","/opt/config_values/git_ask_pass_script.sh","--do-not-fork"]` | Arguments passed to steward binary |
| askPassScript | string | `"#!/bin/bash\nset -u\necho ${VCS_TOKEN}"` | Script which echoes VCS token |
| credentialsSbt | string | `""` | Sbt credentials |
| defaultConf | string | `""` | Default Scala Steward config |
| cron.interval | string | `"@daily"` | cron expression - when to run kubernetes CronJob |
| cron.restartPolicy | string | `"OnFailure"` | Whether to restart cronjob on failure |
| existingSecretName | string | `nil` | If empty, the chart will create the secret containing the vcs token.    If not empty - the already existing secret is used.    The secret should have a field names VCS_TOKEN |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"fthomas/scala-steward"` |  |
| image.tag | string | `"latest"` |  |
| nodeSelector | object | `{}` |  |
| persistence.accessMode | string | `"ReadWriteOnce"` | Access mode of the PVC |
| persistence.enabled | bool | `true` | Whether enable persistent volume to store cache |
| persistence.size | string | `"10Gi"` | Size of the PVC |
| persistence.storageClassName | string | `"standard"` | Storage class |
| repos | string | `"- org/repo-name\n"` |  |
| resources | object | `{}` |  |
| steward.gitAuthorEmail | string | `"steward@example.com"` | Email of the git user |
| steward.gitAuthorName | string | `"steward"` | Name of the git user |
| steward.vcsLogin | string | `""` | VCS login name |
| steward.vcsToken | string | `""` | VCS token |
| tolerations | list | `[]` |  |

## Credits

Based on an internal tool created by [Kasper Kondzielski](https://github.com/ghostbuster91).

Happy helming!
