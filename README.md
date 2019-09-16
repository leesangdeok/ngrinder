# nGrinder
직접 스크립트를 작성하여 부하테스트를 진행하고 리포트로 결과를 확인할 수 있다.

## Prerequisites
1.5.0 or above

## Two major components
#### __controller__ : 성능 테스트를 위해 스크립트를 작성할 수 있는 웹어플리케이션

docker image 
```
$ docker pull ngrinder-controller:3.4
```

start controller
```
docker run -d -v ~/ngrinder-controller:/opt/ngrinder-controller -p 80:80 -p 16001:16001 -p 12000-12009:12000-12009 ngrinder-controller:3.4
``` 

Port info. : 
* __80__: Default controller web UI port.

* __9010-9019__: agents connect to the controller cluster through these ports.

* __12000-12029__: controllers allocate stress tests through these ports.


#### __agent__ : 가상 유저 생성기

docker image 
```
$ docker pull ngrinder/agent:3.4
```

start agent 
```
# docker run -v ~/ngrinder-agent:/opt/ngrinder-agent -d ngrinder/agent:3.4 {controller_ip}:{controller_web_port}
docker run -v ~/ngrinder-agent:/opt/ngrinder-agent -d ngrinder/agent:3.4 127.0.0.1:80
``` 
