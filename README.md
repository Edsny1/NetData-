
![68747470733a2f2f692e68697a6c69726573696d2e636f6d2f6b7134683776662e706e67](https://github.com/Edsny1/NetData-/assets/98622870/9a1d1a2e-3028-4de7-a409-ee4c19e403cc)


Running netdata latest version on ubuntu 22.04

Netdata sunucu izleme yazılımıdır. Netdata ekibi ubuntu 18 üzerine destek vermiyor. Ubuntu 22.04 üzerine yüklemek için Netdata 1.3.1 kullanabiliyorsunuz.

Bu projede, Ubuntu 22.04 veya daha yüksek versiyonlarına, [Netdata en son versiyonu](https://hub.docker.com/r/netdata/netdata/tags) (şimdi 1.45) yükleme imkanı bulacaksınız.

Terminale aşağıdaki komutu giriniz

```
docker pull netdata/netdata:latest
```

sonra da

```
docker run -d --name=netdata \
  --pid=host \
  --network=host \
  -v netdataconfig:/etc/netdata \
 -v netdatalib:/var/lib/netdata \
  -v netdatacache:/var/cache/netdata \
  -v /etc/passwd:/host/etc/passwd:ro \
  -v /etc/group:/host/etc/group:ro \
  -v /etc/localtime:/etc/localtime:ro \
  -v /proc:/host/proc:ro \
  -v /sys:/host/sys:ro \
  -v /etc/os-release:/host/etc/os-release:ro \
  -v /var/log:/host/var/log:ro \
  -v /var/run/docker.sock:/var/run/docker.sock:ro \
  --restart unless-stopped \
  --cap-add SYS_PTRACE \
  --cap-add SYS_ADMIN \
  --security-opt apparmor=unconfined \
  netdata/netdata
```

Şimdi gidip kendi local ip nizden izleyebilirsiniz http://192.168.0.20:19999/ gibi Dışarıdan harici ip den izlemek için ufw allow 19999 ve modem ise 19999 portunu açmanız gerekecektir

![68747470733a2f2f692e68697a6c69726573696d2e636f6d2f327179733478792e706e67](https://github.com/Edsny1/NetData-/assets/98622870/1345fe1a-7e31-4209-a7a6-4e66b87c70f9)

Uygulama size email veya [mobil uygulaması](https://play.google.com/store/apps/details?id=cloud.netdata.android&gl=TR) üzerinden bildirim gönderebiliyor. 

