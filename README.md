# yh-RADIUS
yh-radius é uma implementação de protocolo radius desenvolvida usando a linguagem golang. Atualmente está adaptado para Huawei, Cisco, ZTE, RouterOS (MikroTik) e protocolos padrão. Outros protocolos de fabricantes serão adicionados no futuro.

## Compilar e instalar

Você pode usar a versão de lançamento já lançada no github

Você também pode compilar o pacote de instalação para a plataforma correspondente: Por exemplo, na plataforma Windows:
```  
    cd source_code_dir
    set CGO_ENABLED=0
    set GOOS=linux
    set GOARCH=amd64 
    go build
```

### release versão:

O sistema é desenvolvido separando o front-end e o back-end: back-end do servidor radius + front-end do sistema de gerenciamento

O front-end do sistema de gerenciamento precisa ser executado em um ambiente de servidor web (nginx, tomcat, etc.) O back-end do servidor radius é uma versão binária compilada que pode ser executada da seguinte forma:

## yh-radius introdução do sistema

Após a conclusão da compilação, copie os seguintes diretórios ou arquivos para o diretório em execução: yh-radius, atributos, config, startup.sh, shutdown.sh

A estrutura do diretório é a seguinte:
 
    yh-radius
        |___ attributes
  
        |___ config
  
        |__ yh-radius
    
        |__ startup.sh
    
        |__ shutdown.sh

#### 在Linux系统中运行系统: 

> chmod +x startup.sh

> ./startup.sh

#### Linux系统中停止系统:

> chmod +x shutdown.sh

> ./shutdown.sh

## 配置文件解释

| 字段名 | 默认值 | 类型 | 描述 |
| ------| ------ | ------ | ----- |
| auth.port | 1812 | int |  radius认证端口  |
| acct.port | 1813 | int |  radius计费端口  |
| encrypt.key | 支持16,24,32长度的十六进制字符串 | string |  用于加密用户密码  |
| radius.session.timeout | 604800 | int | 默认一周的秒数  |
| limiter.limit | 100 | int | 用于限制每次添加到令牌桶中的token数量，间接控制go协程并发数量, 服务器环境可根据实际情况调整 |
| limiter.burst | 1000 | int | 用于限制最多的可用token数量,间接控制go协程并发数量,服务器环境可根据实际情况调整  |
| product.stage | debug | string | 控制gin日志，sql显示；可选值：test,debug,release 发布生产环境时请修改此配置为：release  |

## 数据库表结构
数据库表定义在radius-v2.sql中

## 使用radius-web管理平台
这里有一个可用的radius管理平台，实现了用户管理，套餐管理，nas管理，在线用户管理，管理员管理，角色管理等[yh-radius-web](https://github.com/cometowell/radius-web.git)
web平台默认的登陆用户: admin/123456

![首页](https://github.com/cometowell/yh-radius/raw/master/document/index.png)
![用户管理](https://github.com/cometowell/yh-radius/raw/master/document/user.png)
![套餐管理](https://github.com/cometowell/yh-radius/raw/master/document/product.png)
![在线用户管理](https://github.com/cometowell/yh-radius/raw/master/document/online.png)
![系统设置](https://github.com/cometowell/yh-radius/raw/master/document/system.png)
![角色管理](https://github.com/cometowell/yh-radius/raw/master/document/role.png)


## 许可协议
[MIT](https://mit-license.org/)
