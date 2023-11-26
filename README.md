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

#### Executando o sistema em um sistema Linux:

> chmod +x startup.sh

> ./startup.sh

#### Parando o sistema no sistema Linux:

> chmod +x shutdown.sh

> ./shutdown.sh

## Explicação do arquivo de configuração

| Nome do campo | Valor padrão | Tipo | Descrição |
| ------| ------ | ------ | ----- |
| auth.port | 1812 | int |  porta de autenticação radius  |
| acct.port | 1813 | int |  porta de contas radius  |
| encrypt.key | Suporta strings hexadecimais com comprimentos de 16, 24 e 32 | string |  Usado para criptografar senhas de usuários  |
| radius.session.timeout | 604800 | int | Número padrão de segundos em uma semana  |
| limiter.limit | 100 | int | Usado para limitar o número de tokens adicionados ao token bucket a cada vez e controlar indiretamente o número de corrotinas Go simultâneas.O ambiente do servidor pode ser ajustado de acordo com a situação real. |
| limiter.burst | 1000 | int | Usado para limitar o número máximo de tokens disponíveis e controlar indiretamente o número de corrotinas go simultâneas.O ambiente do servidor pode ser ajustado de acordo com a situação real. |
| product.stage | debug | string | Controle gin log, exibição sql; valores opcionais: teste, depuração, liberação. Ao liberar o ambiente de produção, modifique esta configuração para: liberação |

## Estrutura da tabela do banco de dados
A tabela do banco de dados é definida em radius-v2.sql

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
