---
description: https://medium.com/swlh/sonarqube-sonarscanner-setup-1a633b654828
---

# Sonar Qube

Sonnar scanner merupakan _software_ untuk mengecek _coverage_ dari unit testing. Idealnya unit test perlu di atas 80 %.

1. Buat sonnar project di dalam folder aplikasi Golang dengan nama sonar-project.properties.

<figure><img src=".gitbook/assets/1 (3).png" alt=""><figcaption></figcaption></figure>

```properties
sonar.projectKey=Sales-Go
sonar.projectName=Sales-Go

sonar.projectVersion=1.0
# source of program
sonar.sources=.
# source of program that will not be scanned by sonnar scanner
sonar.exclusions=**/helper/*,**/docs/**, **/mocks/**
sonar.ts.tslint.configPath=tslint.json
sonar.typescript.lcov.reportPaths=coverage/lcov.info

# testing needs config
sonar.test.inclusions=**/*_test.go
sonar.test.exclusions=**main.go, **/helper/*,**/docs/**, **/mocks/**
sonar.go.coverage.reportPaths=reports/result.out
```

Buat folder reports dan jalankan _command_ berikut untuk memperoleh file result.out.

```bash
go test ./... -v -coverpkg=./... -coverprofile=reports/result.out
```

Jika ingin generate result.html, bisa tambahkan _command_ go tool cover berikut.

```bash
go test ./... -v -coverpkg=./... -coverprofile=reports/result.out && go tool cover -html reports/result.out -o reports/result.html
```
