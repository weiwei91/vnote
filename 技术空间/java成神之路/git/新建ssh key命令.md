# 新建ssh key命令

有时候github推送失败，是由于sshkey 失效，添加也比较简单


```
cd  ~/.ssh
ssh-keygen -t rsa -C weismart1@gmail.com
cat id_rsa.pub  
ssh -T git@github.com 
ssh-add id_rsa


```