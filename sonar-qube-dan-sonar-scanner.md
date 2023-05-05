---
description: https://medium.com/swlh/sonarqube-sonarscanner-setup-1a633b654828
---

# Sonar Qube dan Sonar Scanner

## Sonar Scanner

Command untuk melakukan generate result.out dan result.html di project golang

```bash
go test ./... -v -coverpkg=./... -coverprofile=reports/result.out
```

```bash
go test ./... -v -coverpkg=./... -coverprofile=reports/result.out && go tool cover -html reports/result.out -o reports/result.html
```
