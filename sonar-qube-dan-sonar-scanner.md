---
description: https://medium.com/swlh/sonarqube-sonarscanner-setup-1a633b654828
---

# Sonar Qube dan Sonar Scanner

## Instalasi Sonar Qube



## Instalasi Sonar Scanner

```
sonar-scanner.bat -D"sonar.projectKey=Sales-Go" -D"sonar.sources=." -D"sonar.host.url=http://localhost:9000" -D"sonar.token=sqp_26f1f44ff1eea240f5fea0a2bb1a8550c471904b"
```



```bash
go test ./... -v -coverpkg=./... -coverprofile=reports/result.out
```
