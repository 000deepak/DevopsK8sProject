# devops-automation

## Create EC2
1. select ubuntu t2.medium & create ec2
2. take access in gitbash using ssh
3. sudo -i

## Install Java
```ubuntu
sudo apt update
sudo apt install openjdk-11-jdk -y
```

## Add jenkin Repository
1. Start by importing the GPG key. The GPG key verifies package integrity but there is no output. Run:
```ubuntu
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc &gt; /dev/null
```

2. Add the Jenkins software repository to the source list and provide the authentication key:
```ubuntu
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list &gt; /dev/null
```

## Install Jenkins
```ubuntu
sudo apt update
sudo apt install jenkins -y
sudo systemctl status jenkins
```

1. check running status of jenkin
2. open public DNS in browser with port 8080
> If it is not opening then go to security group and edit inbound rulesmand All traffic rule.
3. Now copy the password path given on jenkins console in browser and do cat <path> in git bash
4. U will get password, copy & paste the password in console and login
5. install suggested plugins
6. Create admin user
7. Give url and start using jenkins

## Install Docker
```
apt update -y
docker --version
apt install docker.io
```

## Create DockerHub Account and Repo
* add username and password
* create one repo,here repo created & userd is springboot


## Give Access for Jenkins to Docker
> add jenkins to docker users group, other wise jenkins will not be able to use docker commands

```
usermod -a -G docker jenkins
```

## Jenkin Pipelins
* New item of type pipeline
> maven is required to build the project
* Go to Manage Genkins -> Global Tool Configuration -> Maven -> Add Maven -> Give Name and Select Version.
1. Stage 1 : Build Maven<br>
>give repository address and build maven
```ubuntu
mvn clean install
```

2. Stage 2 : Build docker image

```ubuntu
docker build -t springboot_app .
```
> sprigboot_app is image name

3. Stage 3 : Push Image to Hub<br>
a. login to dockerHub using username & password<br>

```ubuntu
docker login -u 000deepak -p ${dockerhubpwd}
```
b. push image to hub<br>

```ubuntu
docker push 000deepak/springboot:latest
```
> 000deepak is username & springboot is repo name & latest tag
## FINAL



## Springboot App
* create a simple springboot app,by default it will run on port 8080.
* create a repository on github and push the app to repository.

