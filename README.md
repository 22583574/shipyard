1：加速器
修改docker配置文件，添加下面一行，加速设置

[root@node-1 ~]# vim /etc/sysconfig/docker

......

ADD_REGISTRY='--add-registry 62kr37rk.mirror.aliyuncs.com'

2:sh shipyard-deploy.sh

3:修改下面配置

docker 添加以下信息  
cat /lib/systemd/system/docker.service

-H=unix:///var/run/docker.sock -H=tcp://0.0.0.0:2375 \

systemctl daemon-reload
重启
systemctl restart docker  






Docker 排坑之旅(一):windows下不能挂载文件夹进container

既然是git-bash尝试补全造成的问题，那就想办法不要补齐或者强制转义。stackoverflow的高分解答表示，在path前加/可以实现跳过path的书写转义规定。那我们来试试看。
　　
错误重现中的第二点，也是用/开始的，显然不对。那我们在前面再加一个/
　　
-v //var/run/docker.sock:/var/run/docker.sock \