## 리눅스용 오라클 설치 파일
```
https://www.oracle.com/technetwork/database/database-technologies/express-edition/downloads/xe-prior-releases-5172097.html

https://dlgkstjq623.tistory.com/413
```
```
# apt install -y alien libaio1 unixodbc bc unzip

파일질라 새 사이트 -> public key > 프로토콜 : SFTP > 로그인 유형 

/home/ubuntu 폴더에 다운로드 받은 linux용 oracle zip 파일 전송

/home/ubuntu# unzip -x oracle-xe-11.2.0-1.0.x86_64.rpm.zip

/home/ubuntu# alien --scripts -d oracle-xe-11.2.0-1.0.x86_64.rpm (오래걸림 한 5분)

## 생성된 deb 파일을 실행하여 오라클 DB 설치
/home/ubuntu# dpkg --install oracle*.deb

/home/ubuntu# /etc/init.d/oracle-xe configure

1234 1234
```
## 환경변수 설정
```
vim ~/.bashrc 
export ORACLE_HOME=/u01/app/oracle/product/11.2.0/xe 
export ORACLE_SID=XE 
export NLS_LANG=`$ORACLE_HOME/bin/nls_lang.sh` 
export ORACLE_BASE=/u01/app/oracle
export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
export PATH=$ORACLE_HOME/bin:$PATH
source ~/.bashrc  
```
## 오라클 접속
```
sqlplus system
1234

CREATE USER happybox IDENTIFIED BY 1234;

GRANT ALL TO happybox IDENTIFIED BY 1234 WITH GRANT OPTION;

grant create session to 유저이름;

admin 계정으로 접속 conn sys as sysdba;

grant all privileges to happybox;

=======

GRANT CREATE ANY TABLE TO happybox;
grant unlimited tablespace to happybox;
```
