# php7-wxwork-sdk
支持高并发拉取会话存档的PHP扩展包 【CentOs7.x系统】

## 官方包，获取会话内容SDK(C_sdk)
https://developer.work.weixin.qq.com/document/path/91774

## 结合pangdahua的扩展包（php7-wxwork-finance-sdk-1.2.0）
https://github.com/pangdahua/php7-wxwork-finance-sdk

## 依赖
企业微信提供的sdk;

PHP VERSION >= 7.0

openssl扩展

## 安装步骤及要求
```
git clone git@github.com:hzp0szl/php7-wxwork-sdk.git
```

```
cd php7-wxwork-sdk/php7-wxwork-finance-sdk-1.2.0
```

```
INSATLL_PATH_PATH/bin/phpize
```

```
./configure --with-php-config=$INSTALL_PHP_PATH/php-config --with-wxwork-finance-sdk=$WXWORK_FINANCE_C_SDK_PATH
```
root目录列子 ./configure --with-php-config=/usr/local/php/bin/php-config --with-wxwork-finance-sdk=/root/php7-wxwork-sdk/C_sdk

```
make && make install
```

打开扩展
INSATLL_PATH_PATH/etc/php.d
新增01-wxwork-finance-sdk.ini文件
```
extension=wxwork_finance_sdk.so
```

## 问题
 1. free(): invalid pointer
   * 定位intl扩展的冲突问题  php -m |grep intl 重新编译php，取消intl扩展
Cd /www/server/panel/install
vim php.sh
Php74  的./configure --disable-intl
sh /www/server/panel/install/php.sh install 7.4
   
  2. 与swoole的扩展冲突
   * 需要将wxwork_finance_sdk.so 放在swoole扩展之前