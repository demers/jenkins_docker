Dockerfile inspiré de https://tripdubroot.com/jenkins-docker-in-docker-dind-2040cc90eeab (site qui n'existe plus maintenant).

1. Installation de Jenkins LTS
2. Installation de Docker
3. Installation de Docker compose
4. Jenkins roule dans le compte "jenkins"

Il faut partir le serveur comme suit:

```
docker build -t jenkins_docker .

docker run -itd -u root --name jenkins -p 8080:8080 -p 50000:50000 -v /var/run/docker.sock:/var/run/docker.sock -v /root/jenkins:/var/jenkins_home jenkins_docker
```

pour avoir la configuration Jenkins dans /root/jenkins

ou

```
docker run -itd -p 8080:8080 -p 50000:50000 -v /var/run/docker.sock:/var/run/docker.sock -v ~/jenkins/jenkins_home:/var/jenkins_home --name jenkins jenkins_docker
```

pour avoir la configuration Jenkins dans ~/jenkins/jenkins_home

Au démarrage, le serveur Jenkins est accessible à l'adresse
http://localhost:8080

Il se peut que vous aillez à ajouter le paramètre --net=host au démarrage.
