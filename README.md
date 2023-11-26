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

## Use a plataforma de gerenciamento radius-web
Há uma plataforma de gerenciamento radius disponível aqui, que implementa gerenciamento de usuários, gerenciamento de pacotes, gerenciamento nas, gerenciamento de usuários online, gerenciamento de administrador, gerenciamento de funções, etc. O usuário de login padrão da plataforma web yh-radius-web é: admin/123456

![primeira página](https://github.com/cometowell/yh-radius/raw/master/document/index.png)
![Gerenciamento de usuários](https://github.com/cometowell/yh-radius/raw/master/document/user.png)
![Gerenciamento de pacotes](https://github.com/cometowell/yh-radius/raw/master/document/product.png)
![Gerenciamento de usuários on-line](https://github.com/cometowell/yh-radius/raw/master/document/online.png)
![Configurações de sistema](https://github.com/cometowell/yh-radius/raw/master/document/system.png)
![gerenciamento de funções](https://github.com/cometowell/yh-radius/raw/master/document/role.png)


## E é isto ai!
[MIT](https://mit-license.org/)
