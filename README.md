# SonarQube Scanner for linux

Runs the SonarQube scanner on a linux machine. This uses the sonarqube zip file and embeded java. No docker or java install required.

Perfect for hosted or self-hosted runners

## Usage

An example workflow to run SonarQube scan task scan and upload results to sonarqube.

```yaml
name: Scan code

on: [push]

env:
  SONARQUBE_PROJECT_KEY: ${{ github.event.repository.owner.login }}:${{ github.event.repository.name }}
  SONARQUBE_PROJECT_NAME: ${{ github.event.repository.owner.login }}:${{ github.event.repository.name }}

jobs:
  scan:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2

    - name: Scan
      uses: jimseiwert/sonarqube-scanner-linux@v1.0
      with:
        host-url: ${{ secrets.sonarqube_url }}
        token: ${{ secrets.sonarqube_token }}
        project-key: ${{ env.SONARQUBE_PROJECT_KEY }}
        project-name: ${{ env.SONARQUBE_PROJECT_NAME }}
```

