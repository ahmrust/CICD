# Домашнее задание к занятию "Что такое DevOps. СI/СD" - `Ахмадеев Рустам`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

```
Поле для вставки кода...
Вывод на консоль

Started by user admin
Running as SYSTEM
Building in workspace /var/lib/jenkins/workspace/my_pipe1
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/my_pipe1/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/ahmrust/sdvps-materials # timeout=10
Fetching upstream changes from https://github.com/ahmrust/sdvps-materials
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
 > git fetch --tags --force --progress -- https://github.com/ahmrust/sdvps-materials +refs/heads/*:refs/remotes/or>
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision 223dbc3f489784448004e020f2ef224f17a7b06d (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
Commit message: "Update README.md"
 > git rev-list --no-walk 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
[my_pipe1] $ /bin/sh -xe /tmp/jenkins17038371439569866021.sh
+ go test .
ok      github.com/netology-code/sdvps-materials        (cached)
+ docker build . -t ubuntu-bionic:8082/hello-world:v13
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 350B done
#1 DONE 0.1s

#2 [internal] load metadata for docker.io/library/golang:1.16
#2 DONE 0.3s

#3 [internal] load metadata for docker.io/library/alpine:latest
#3 DONE 0.3s

#4 [internal] load .dockerignore
#4 transferring context: 2B done
#4 DONE 0.0s

#5 [stage-1 1/3] FROM docker.io/library/alpine:latest@sha256:c5b1261d6d3e43071626931fc004f70149baeba2c8ec672bd4f27>
#5 DONE 0.0s

#6 [builder 1/4] FROM docker.io/library/golang:1.16@sha256:5f6a4662de3efc6d6bb812d02e9de3d8698eea16b8eb7281f03e6f3>
#6 DONE 0.0s

#7 [internal] load build context
#7 transferring context: 13.17kB 0.1s done
#7 DONE 0.1s

#8 [builder 2/4] WORKDIR /go/src/github.com/netology-code/sdvps-materials
#8 CACHED
#9 [builder 3/4] COPY . ./
#9 CACHED

#10 [builder 4/4] RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app .
#10 CACHED

#11 [stage-1 2/3] RUN apk -U add ca-certificates
#11 CACHED

#12 [stage-1 3/3] COPY --from=builder /app /app
#12 CACHED

#13 exporting to image
#13 exporting layers done
#13 writing image sha256:837724be2c14aa837ba55e77108b6cfaeb04c19e35789f8acd056419751cf1e5 0.0s done
#13 naming to ubuntu-bionic:8082/hello-world:v13 0.0s done
#13 DONE 0.0s
Finished: SUCCESS
....

```

![alt text](https://github.com/ahmrust/homework-CICD/blob/main/img/1.png)
![alt text](https://github.com/ahmrust/homework-CICD/blob/main/img/2.png)
---

### Задание 2

`Приведите ответ в свободной форме........`

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота 2](ссылка на скриншот 2)`
'![alt text](https://github.com/ahmrust/homework-CICD/blob/main/img/4.png)'

---

### Задание 3

Поле для вставки кода...

pipeline {
 agent any
 stages {
  stage('Git') {
   steps {git 'https://github.com/ahmrust/sdvps-materials.git'}
  }
  stage('Test') {
   steps {
    sh 'go test .'
   }
  }
  stage('Build') {
   steps {
    sh 'go build -a -installsuffix nocgo -o ./app .'
   }
  }
  stage('Push') {
   steps {
    sh 'curl -v -u admin:admin --upload-file ./app "http:/ubuntu-bionic:8081/repository/my_repo2/app_v$BUILD_NUMBER"'  }
   }
  }
 }
....

Вывод на консоль

Started by user admin
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/my_pipe2.2
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Git)
[Pipeline] git
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/my_pipe2.2/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/ahmrust/sdvps-materials.git # timeout=10
Fetching upstream changes from https://github.com/ahmrust/sdvps-materials.git
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
 > git fetch --tags --force --progress -- https://github.com/ahmrust/sdvps-materials.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/master^{commit} # timeout=10
Checking out Revision 223dbc3f489784448004e020f2ef224f17a7b06d (refs/remotes/origin/master)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git branch -D master # timeout=10
 > git checkout -b master 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
Commit message: "Update README.md"
 > git rev-list --no-walk 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Test)
[Pipeline] sh
+ go test .
ok  	github.com/netology-code/sdvps-materials	(cached)
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] sh
+ go build -a -installsuffix nocgo -o ./app .
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Push)
[Pipeline] sh
+ curl -v -u admin:admin --upload-file ./app http:/ubuntu-bionic:8081/repository/my_repo2/app_v57
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0*   Trying 127.0.0.1:8081...
* Connected to ubuntu-bionic (127.0.0.1) port 8081 (#0)
* Server auth using Basic with user 'admin'
> PUT /repository/my_repo2/app_v57 HTTP/1.1
> Host: ubuntu-bionic:8081
> Authorization: Basic YWRtaW46YWRtaW4=
> User-Agent: curl/7.81.0
> Accept: */*
> Content-Length: 1864162
> Expect: 100-continue
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 100 Continue
} [65536 bytes data]
* We are completely uploaded and fine
* Mark bundle as not supporting multiuse
< HTTP/1.1 201 Created
< Date: Sun, 17 Mar 2024 19:37:01 GMT
< Server: Nexus/3.66.0-02 (OSS)
< X-Content-Type-Options: nosniff
< Content-Security-Policy: sandbox allow-forms allow-modals allow-popups allow-presentation allow-scripts allow-top-navigation
< X-XSS-Protection: 1; mode=block
< Content-Length: 0
< 

100 1820k    0     0  100 1820k      0  4131k --:--:-- --:--:-- --:--:-- 4175k
100 1820k    0     0  100 1820k      0  4130k --:--:-- --:--:-- --:--:-- 4175k
* Connection #0 to host ubuntu-bionic left intact
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
....
```

`При необходимости прикрепитe сюда скриншоты`
![alt text](https://github.com/ahmrust/homework-CICD/blob/main/img/7.png)
![alt text](https://github.com/ahmrust/homework-CICD/blob/main/img/8.png)

---
