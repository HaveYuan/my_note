# 服务器配置ssl步骤（apache服务器）
### 1.去腾讯云或阿里云购买ssl证书，或者使用腾讯云的域名型（DV）免费SSL证书（https://cloud.tencent.com/document/product/400/8422）
### 2.将下载好的证书解压后得到不同服务器类型的ssl证书，分别是Apache,IIS,Nginx,Tomcat，这里我们选择Apache文件夹内的文件，它包含三个文件
* `2_www.070703.club.crt`     (服务器证书)
* `3_www.070703.club.key`   (私钥文件）如果为空请将生成CSR时保存的私钥内容粘贴在文件中
* `1_root_bundle.crt`  (根证书链）
### 3.找到apache的安装目录，找到php.ini文件查看是否开启了ssl模块，查看是否存在extension=php_openssl.dll，如果有就去掉前面的#。
### 4.打开apache目录下的conf文件夹下的httpd.conf文件，添加如下配置
* LoadModule socache_shmcb_module modules/mod_socache_shmcb.so 
* LoadModule ssl_module modules/mod_ssl.so
* Include conf/extra/httpd-ssl.conf
### 5.打开extra文件夹下的httpd-ssl.conf文件，添加如下配置
 Listen 443  
 `<VirtualHost *:443>`  
  `SSLEngine on`  
  `SSLProtocol all -SSLv2 -SSLv3`  
  `SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5`  
  `SSLCertificateFile "C:/AppServ/Apache24/conf/ssl/2_www.070703.club.crt"`  
  `SSLCertificateKeyFile "C:/AppServ/Apache24/conf/ssl/3_www.070703.club.key"`  
  `SSLCertificateChainFile "C:/AppServ/Apache24/conf/ssl/1_root_bundle.crt"`  
  `DocumentRoot  "C:/AppServ/www"`  
  `<Directory />`  
    `  Options +Indexes +FollowSymLinks +ExecCGI`  
    `  AllowOverride All`  
    `  Order allow,deny`  
    `  Allow from all`  
    `  Require all granted`  
  `</Directory>`  
  `</VirtualHost>`  
  目录要写完整路径，`（www.070703.club）`是自己的域名。
  ### 6.将之前的三个证书文件放入conf/ssl文件夹内。
