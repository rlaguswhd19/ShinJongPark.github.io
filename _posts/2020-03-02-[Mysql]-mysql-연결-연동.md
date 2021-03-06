---
title: "[MySql] AWS Mysql 설치 및 원격접속"
tags: "Mysql"
author : ""
article_header:
  type: overlay
  theme: dark
  background_color: '#123'
  background_image: false
---
<br>

#### 1. Mysql 설치

```shell
#apt-get 업데이트 
sudo apt-get update 

#mysql 설치 
sudo apt-get 
install mysql-server 

# mysql 보안 설정 

sudo mysql_secure_installation
```

<br> 

#### 2. Mysql 비밀번호 설정

```shell
# mysql 접속 초기 비밀번호는 없음 
sudo mysql -u root -p  

# mysql database 접속 
> use mysql;  

# 비밀번호 변경 
> alter user 'root'@'localhost' identified with mysql_native_password by '변경할 비밀번호';  

# 변경사항 저장 
> flush privileges;
```

<br>

#### 3. 외부 접속 사용자 계정 생성

```shell
sudo mysql -u root -p  
> create user '생성할 유저이름'@'허용할 서버 (모두 허용시 %)' identified by '접속 비밀번호';  
> grant all privileges on '접속 허용할 db (모두 허용시 *)'.* to '생성한 유저이름'@'허용할 서버';  
> flush privileges;  

# mysql 접속 종료 
exit  

# mysql 서버 재시작 
sudo /etc/init.d/mysql restart
```

<br>

#### 4. 외부 접속 허용 환경 설정

```shell
sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
bind-address = 127.0.0.1  => bind-address = 0.0.0.0
또는 주석처리
#bind-address = 127.0.0.1

mysql 서버 재시작
sudo /etc/init.d/mysql restart
```

<br>

#### 5. WrokBench 원격접속

![workbench](https://user-images.githubusercontent.com/46040293/75642977-c9d57400-5c80-11ea-8c2b-0a08edd19ab2.PNG)