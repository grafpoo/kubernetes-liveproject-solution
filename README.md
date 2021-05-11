# kubernetes-postgres-solution

## create spring boot image

```sh
mvn spring-boot:build-image
```

the image will show up in your local registry

```sh
❯ docker images
REPOSITORY                         TAG                     IMAGE ID       CREATED        SIZE
paketobuildpacks/run               base-cnb                793c0420709a   45 hours ago   87.7MB
gcr.io/k8s-minikube/kicbase        v0.0.20                 c6f4fc187bc1   4 weeks ago    1.09GB
restapi                            0.0.1-SNAPSHOT          740a40e9d44c   41 years ago   288MB
gcr.io/paketo-buildpacks/builder   base-platform-api-0.3   bbb944e79519   41 years ago   590MB
```

now you need to tag the image and push it to a registry. i am using docker hub, so i only need to add my use my username:

```sh
docker tag restapi:0.0.1-SNAPSHOT grafpoo/restapi:latest
```

and push:

```sh
❯ docker push grafpoo/restapi:latest
The push refers to repository [docker.io/grafpoo/restapi]
1daae206ee97: Pushed
20e1cf6014bd: Pushed
43b7b01c45e1: Pushed
6763b99e3792: Layer already exists
aa7edff7133e: Layer already exists
7a7ffa0a3f6c: Layer already exists
7fbc97c38fad: Layer already exists
0b18b1f120f4: Layer already exists
7074331958bf: Pushed
ec0381c8f321: Layer already exists
230fbfb3ce9c: Pushed
cbe849c7f40e: Pushed
32fe97cac33e: Mounted from paketobuildpacks/run
ceb7a5edaf89: Mounted from paketobuildpacks/run
cd2f00bf3849: Mounted from paketobuildpacks/run
8cafc6d2db45: Mounted from paketobuildpacks/run
a5d4bacb0351: Mounted from paketobuildpacks/run
5153e1acaabc: Mounted from paketobuildpacks/run
latest: digest: sha256:e78a45c3e68d4dc8fb1471c677c834160b125ac71434eb97c64471a9228ef8f4 size: 4087
```