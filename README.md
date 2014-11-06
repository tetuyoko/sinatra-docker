sinatra-docker
==============

* Dockerの色々なテスト

# Install
 * [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
 * [Vagrant](https://www.vagrantup.com/downloads.html$)
 * [boot2docker](http://boot2docker.io/)
 * [Docker](https://docs.docker.com/installation/#installation)
 * [fig](http://www.fig.sh/)

```
 % boot2docker start
 % $(boot2docker shellinit)
 % git clone git@github.com:tetuyoko/sinatra-docker.git
 % cd sinatra-docker/fig_python
 % fig up -d
 % open http://$(boot2docker ip 2>/dev/null):5000/
```

