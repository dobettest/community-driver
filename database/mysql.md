# 创建mysql集群
## mysql_1
| 逻辑库 | 备注 | 具体用途 |
|----|---|---|
|hxds_cst|客户逻辑库|客户信息、罚款等|
|hxds_dr|司机逻辑库|司机信息、实名认证、钱包、罚款等|
|hxds_mis|mis系统逻辑库|PC管理系统所用的信息表|
|hxds_rule|规则逻辑库|代驾费计算、分账计算、取消规则等|
```bash
docker run -it -d --name mysql_1 -p 12001:3306 \
--net mynet --ip 172.18.0.2 \
-m 400m -v /root/mysql_1/data:/var/lib/mysql \
-v /root/mysql_1/config:/etc/mysql/conf.d \
-e MYSQL_ROOT_PASSWORD=mysql2023 \
-e TZ=Asia/Shanghai --privileged=true \
mysql:8.0.23 \
--lower_case_table_names=1
```
## mysql_2
| 逻辑库 | 备注 | 具体用途 |
|----|---|---|
|hxds_cst|客户逻辑库|客户信息、罚款等|
|hxds_dr|司机逻辑库|司机信息、实名认证、钱包、罚款等|
|hxds_rule|规则逻辑库|代驾费计算、分账计算、取消规则等|
```bash
docker run -it -d --name mysql_2 -p 12002:3306 \
--net mynet --ip 172.18.0.3 \
-m 400m -v /root/mysql_2/data:/var/lib/mysql \
-v /root/mysql_2/config:/etc/mysql/conf.d \
-e MYSQL_ROOT_PASSWORD=mysql2023 \
-e TZ=Asia/Shanghai --privileged=true \
mysql:8.0.23 \
--lower_case_table_names=1
```

## mysql_3
| 逻辑库 | 备注 | 具体用途 |
|----|---|---|
|hxds_odr|订单逻辑库|订单、账单、好评、分账等|
|hxds_vhr|代金券逻辑库|代金券、领取情况、使用情况等|
```bash
docker run -it -d --name mysql_3 -p 12003:3306 \
--net mynet --ip 172.18.0.4 \
-m 400m -v /root/mysql_3/data:/var/lib/mysql \
-v /root/mysql_3/config:/etc/mysql/conf.d \
-e MYSQL_ROOT_PASSWORD=mysql2023 \
-e TZ=Asia/Shanghai --privileged=true \
mysql:8.0.23 \
--lower_case_table_names=1
```

## mysql_4
| 逻辑库 | 备注 | 具体用途 |
|----|---|---|
|hxds_odr|订单逻辑库|订单、账单、好评、分账等|
|hxds_vhr|代金券逻辑库|代金券、领取情况、使用情况等|
```bash
docker run -it -d --name mysql_4 -p 12004:3306 \
--net mynet --ip 172.18.0.5 \
-m 400m -v /root/mysql_4/data:/var/lib/mysql \
-v /root/mysql_4/config:/etc/mysql/conf.d \
-e MYSQL_ROOT_PASSWORD=mysql2023 \
-e TZ=Asia/Shanghai --privileged=true \
mysql:8.0.23 \
--lower_case_table_names=1
```
## mysql_5
```bash
docker run -it -d --name mysql_5 -p 12005:3306 \
--net mynet --ip 172.18.0.6 \
-m 400m -v /root/mysql_5/data:/var/lib/mysql \
-v /root/mysql_5/config:/etc/mysql/conf.d \
-e MYSQL_ROOT_PASSWORD=mysql2023 \
-e TZ=Asia/Shanghai --privileged=true \
mysql:8.0.23 \
--lower_case_table_names=1
```

ShardingSphere
```bash
docker run -it --name ss -p 3307:3307 \
--net mynet --ip=172.18.0.7 \
-m 400m -v /root/ss:/root/ss \
-e TZ=Asia/Shanghai --privileged=true \
openjdk:15.0.2 bash
```