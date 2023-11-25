# Домашнее задание к занятию "Что такое DevOps. СI/СD" - Юлия Лукьянчикова


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw>   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`: done
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя: done
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-home>      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pat>   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.

Желаем успехов в выполнении домашнего задания!

### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

1. Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно: done
2. Установите на машину с jenkins golang: done
3. Используя свой аккаунт на GitHub, сделайте себе форк [репозитория](https://github.com/netology-code/sdvps-materials). В этом же репозитории находится [дополнительный материал для выполнения ДЗ](https://github.com/netology-code/sdvps-materials/blob/main/CICD/8.2-hw.md): [done](https://github.com/lukianchikovai/sdvps-materials)
4. Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта go test . и docker build ..

[Общая ссылка на архив со скриншотами](https://drive.google.com/file/d/1MG-mLvWv3aAes1ucD3Q7wS93UWpzkc6k/view?usp=sharing)

### Результат: 

```
Started by user Julia
Running as SYSTEM
Building in workspace /var/lib/jenkins/workspace/my_pipe_1
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/my_pipe_1/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/lukianchikovai/sdvps-materials.git # timeout=10
Fetching upstream changes from https://github.com/lukianchikovai/sdvps-materials.git
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
 > git fetch --tags --force --progress -- https://github.com/lukianchikovai/sdvps-materials.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision 223dbc3f489784448004e020f2ef224f17a7b06d (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
Commit message: "Update README.md"
 > git rev-list --no-walk 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
[my_pipe_1] $ /bin/sh -xe /tmp/jenkins10269171713768240543.sh
+ /usr/local/go/bin/go test .
ok  	github.com/netology-code/sdvps-materials	(cached)
[my_pipe_1] $ /bin/sh -xe /tmp/jenkins5746265149570744763.sh
+ docker build . -t ubuntu-bionic:8082/hello-world:v17
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 350B done
#1 DONE 0.0s

#2 [internal] load .dockerignore
#2 transferring context: 2B done
#2 DONE 0.0s

#3 [internal] load metadata for docker.io/library/golang:1.16
#3 DONE 1.2s

#4 [internal] load metadata for docker.io/library/alpine:latest
#4 DONE 1.2s

#5 [builder 1/4] FROM docker.io/library/golang:1.16@sha256:5f6a4662de3efc6d6bb812d02e9de3d8698eea16b8eb7281f03e6f3e8383018e
#5 DONE 0.0s

#6 [stage-1 1/3] FROM docker.io/library/alpine:latest@sha256:eece025e432126ce23f223450a0326fbebde39cdf496a85d8c016293fc851978
#6 DONE 0.0s

#7 [internal] load build context
#7 transferring context: 13.19kB 0.0s done
#7 DONE 0.1s

#8 [builder 4/4] RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app .
#8 CACHED

#9 [stage-1 2/3] RUN apk -U add ca-certificates
#9 CACHED

#10 [builder 2/4] WORKDIR /go/src/github.com/netology-code/sdvps-materials
#10 CACHED

#11 [builder 3/4] COPY . ./
#11 CACHED

#12 [stage-1 3/3] COPY --from=builder /app /app
#12 CACHED

#13 exporting to image
#13 exporting layers done
#13 writing image sha256:affc533b35a30176ce0875c14ff16d5cf021a3372a6e890785aec5e95d6a236f done
#13 naming to ubuntu-bionic:8082/hello-world:v17 done
#13 DONE 0.0s
[my_pipe_1] $ /bin/sh -xe /tmp/jenkins17792176652207202167.sh
+ docker login https://ubuntu-bionic:8082 -u admin --password-stdin
+ echo ******
WARNING! Your password will be stored unencrypted in /var/lib/jenkins/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
+ docker push ubuntu-bionic:8082/hello-world:v17
The push refers to repository [ubuntu-bionic:8082/hello-world]
6e89cf6cd3f4: Preparing
0110476d85ba: Preparing
cc2447e1835a: Preparing
6e89cf6cd3f4: Pushed
0110476d85ba: Pushed
cc2447e1835a: Pushed
v17: digest: sha256:3d786a990717054e0f48c43df3e89114619594df38782e2335fb65b0ef1728d7 size: 950
+ docker logout
Removing login credentials for https://index.docker.io/v1/
Finished: SUCCESS

```

---

### Задание 2

1. Создайте новый проект pipeline: done
2. Перепишите сборку из задания 1 на declarative в виде кода: done

### Pipeline:

```
pipeline {
    agent any
    stages {
        stage('Git') {
            steps {
                script {
                    git branch: 'main', url: 'https://github.com/lukianchikovai/sdvps-materials.git'
                }
            }
        }
        
        stage('Test') {
            steps {
                sh '/usr/local/go/bin/go test .'
            }
        }
        
        stage('Build') {
            steps {
                script {
                    sh 'docker build . -t ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER'
                }
            }
        }
        
        stage('Push') {
            steps {
                script {
                    sh 'echo "YLuk9215!" | docker login https://ubuntu-bionic:8082 -u admin --password-stdin && docker push ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER && docker logout'
                }
            }
        }
    }
}
```

### Результат:

```
Started by user Julia
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/my_pipe_2
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Git)
[Pipeline] script
[Pipeline] {
[Pipeline] git
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/my_pipe_2/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/lukianchikovai/sdvps-materials.git # timeout=10
Fetching upstream changes from https://github.com/lukianchikovai/sdvps-materials.git
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
 > git fetch --tags --force --progress -- https://github.com/lukianchikovai/sdvps-materials.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision 223dbc3f489784448004e020f2ef224f17a7b06d (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git branch -D main # timeout=10
 > git checkout -b main 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
Commit message: "Update README.md"
 > git rev-list --no-walk 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Test)
[Pipeline] sh
+ /usr/local/go/bin/go test .
ok  	github.com/netology-code/sdvps-materials	(cached)
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] script
[Pipeline] {
[Pipeline] sh
+ docker build . -t ubuntu-bionic:8082/hello-world:v20
#0 building with "default" instance using docker driver

#1 [internal] load .dockerignore
#1 transferring context: 2B done
#1 DONE 0.1s

#2 [internal] load build definition from Dockerfile
#2 transferring dockerfile: 350B done
#2 DONE 0.1s

#3 [internal] load metadata for docker.io/library/golang:1.16
#3 ...

#4 [internal] load metadata for docker.io/library/alpine:latest
#4 DONE 1.3s

#3 [internal] load metadata for docker.io/library/golang:1.16
#3 DONE 1.3s

#5 [builder 1/4] FROM docker.io/library/golang:1.16@sha256:5f6a4662de3efc6d6bb812d02e9de3d8698eea16b8eb7281f03e6f3e8383018e
#5 DONE 0.0s

#6 [stage-1 1/3] FROM docker.io/library/alpine:latest@sha256:eece025e432126ce23f223450a0326fbebde39cdf496a85d8c016293fc851978
#6 DONE 0.0s

#7 [internal] load build context
#7 transferring context: 112.79kB 0.0s done
#7 DONE 0.1s

#8 [builder 2/4] WORKDIR /go/src/github.com/netology-code/sdvps-materials
#8 CACHED

#9 [builder 3/4] COPY . ./
#9 DONE 0.5s

#10 [builder 4/4] RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app .
#10 DONE 17.1s

#11 [stage-1 2/3] RUN apk -U add ca-certificates
#11 CACHED

#12 [stage-1 3/3] COPY --from=builder /app /app
#12 CACHED

#13 exporting to image
#13 exporting layers done
#13 writing image sha256:affc533b35a30176ce0875c14ff16d5cf021a3372a6e890785aec5e95d6a236f 0.0s done
#13 naming to ubuntu-bionic:8082/hello-world:v20 0.0s done
#13 DONE 0.0s
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Push)
[Pipeline] script
[Pipeline] {
[Pipeline] sh
+ echo *******
+ docker login https://ubuntu-bionic:8082 -u admin --password-stdin
WARNING! Your password will be stored unencrypted in /var/lib/jenkins/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
+ docker push ubuntu-bionic:8082/hello-world:v20
The push refers to repository [ubuntu-bionic:8082/hello-world]
6e89cf6cd3f4: Preparing
0110476d85ba: Preparing
cc2447e1835a: Preparing
cc2447e1835a: Layer already exists
0110476d85ba: Layer already exists
6e89cf6cd3f4: Layer already exists
v20: digest: sha256:3d786a990717054e0f48c43df3e89114619594df38782e2335fb65b0ef1728d7 size: 950
+ docker logout
Removing login credentials for https://index.docker.io/v1/
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```

---

### Задание 3

1. Установите на машину Nexus - done
2. Создайте raw-hosted репозиторий - done
3. Измените pipeline так, чтобы вместо Docker-образа собирался бинарный go-файл. Команду можно скопировать из Dockerfile: done
4. Загрузите файл в репозиторий с помощью jenkins: done

### Pipeline:
 
```
pipeline {
    agent any
    stages {
        stage('Git') {
            steps {
                script {
                    git branch: 'main', url: 'https://github.com/lukianchikovai/sdvps-materials.git'
                }
            }
        }
        
        stage('Test') {
            steps {
                sh '/usr/local/go/bin/go test .'
            }
        }
        
        stage('Build') {
            steps {
                script {
                    sh 'CGO_ENABLED=0 GOOS=linux /usr/local/go/bin/go build -a -installsuffix nocgo -o $WORKSPACE/app .'
                }
            }
        }
        
        stage('Push') {
            steps {
                script {
                    sh 'curl -v -u admin:****** --upload-file $WORKSPACE/app http://158.160.104.228:8081/repository/netology_hw/'
                }
            }
        }
    }
}
```

### Результат: 

```
Started by user Julia
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/my_pipe_2
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Git)
[Pipeline] script
[Pipeline] {
[Pipeline] git
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/my_pipe_2/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/lukianchikovai/sdvps-materials.git # timeout=10
Fetching upstream changes from https://github.com/lukianchikovai/sdvps-materials.git
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
 > git fetch --tags --force --progress -- https://github.com/lukianchikovai/sdvps-materials.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision 223dbc3f489784448004e020f2ef224f17a7b06d (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git branch -D main # timeout=10
 > git checkout -b main 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
Commit message: "Update README.md"
 > git rev-list --no-walk 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Test)
[Pipeline] sh
+ /usr/local/go/bin/go test .
ok  	github.com/netology-code/sdvps-materials	(cached)
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] script
[Pipeline] {
[Pipeline] sh
+ CGO_ENABLED=0 GOOS=linux /usr/local/go/bin/go build -a -installsuffix nocgo -o /var/lib/jenkins/workspace/my_pipe_2/app .
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Push)
[Pipeline] script
[Pipeline] {
[Pipeline] sh
+ curl -v -u admin:***** --upload-file /var/lib/jenkins/workspace/my_pipe_2/app http://158.160.104.228:8081/repository/netology_hw/
*   Trying 158.160.104.228:8081...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to 158.160.104.228 (158.160.104.228) port 8081 (#0)
* Server auth using Basic with user 'admin'
> PUT /repository/netology_hw/app HTTP/1.1
> Host: 158.160.104.228:8081
> Authorization: Basic YWRtaW46WUx1azkyMTUh
> User-Agent: curl/7.81.0
> Accept: */*
> Content-Length: 1864864
> Expect: 100-continue
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 100 Continue
} [65536 bytes data]
* We are completely uploaded and fine

100 1821k    0     0  100 1821k      0  9073k --:--:-- --:--:-- --:--:-- 9060k* Mark bundle as not supporting multiuse
< HTTP/1.1 201 Created
< Date: Sat, 25 Nov 2023 15:09:10 GMT
< Server: Nexus/3.62.0-01 (OSS)
< X-Content-Type-Options: nosniff
< Content-Security-Policy: sandbox allow-forms allow-modals allow-popups allow-presentation allow-scripts allow-top-navigation
< X-XSS-Protection: 1; mode=block
< Content-Length: 0
< 

100 1821k    0     0  100 1821k      0  5734k --:--:-- --:--:-- --:--:-- 5726k
* Connection #0 to host 158.160.104.228 left intact
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```
