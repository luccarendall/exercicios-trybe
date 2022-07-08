#### 
#### Versão do Arquivo Compose
>Todo arquivo docker-compose.yaml deve iniciar com a chave version. Dessa maneira, definimos qual versão deverá ser utilizada pelo Compose para interpretar o arquivo, evitando assim que o docker-compose.yaml fique incompatível com versões mais recentes da ferramenta.

#### Criando Serviços
>No Compose existe o conceito de services. Logo, vamos configurar nosso arquivo Compose com os três serviços que citamos acima.
>
⚠️ A ordem dos serviços neste arquivo não é importante.

>Lembre-se que todo  _container_  é criado a partir de uma  _imagem_. Sendo assim, precisamos especificá-las aos nossos serviços. Temos duas opções para isso:

 1. `image`: especifica uma imagem Docker  **pronta**, seja local ou a
    ser baixada no  _Docker Hub_;   
    
 2. `build`: especifica a  **pasta** 
    contendo um arquivo  `Dockerfile`  a partir do qual o  _Compose_ 
    vai executar o comando  `docker build`  automaticamente.
    
#### Mapeamento de Portas

A próxima configuração importante de cada serviço é o  **mapeamento de portas**. Vimos nos conteúdos anteriores como realizar este mapeamento no comando  `docker run`  ao utilizar a flag  `-p <porta-do-computador>:<porta-do-container>`. Dentro de cada serviço, podemos especificar o  `ports`, que é uma  **lista de mapeamentos de portas entre o computador local e as portas do container**.

>ex: 
**ports:
-- 3000:3000**

⚠️ Anote aí: **o primeiro** parâmetro é sempre a **porta do computador local** e **o segundo** parâmetro é a **porta exposta no container**.

#### Configurando uma política de reinicialização

Seu uso é  **simples**! Dizemos ao  _Compose_  o que ele deve fazer caso um container pare sua execução, de maneira automática! Devemos configurar este comportamento através da chave  `restart`.

O  _Compose_  possui quatro políticas de reinicialização, sendo elas:

-   `no`  : define que o container não reiniciará automaticamente (Padrão);
-   `on-failure`: define que o container será reiniciado caso ocorra alguma falha apontada pelo  `exit code`, diferente de zero;
-   `always`: especifica que sempre que o serviço parar, seja por um falha ou porque ele simplesmente finalizou sua execução, ele deverá ser reiniciado;
-   `unless-stopped`: define que o container sempre será reiniciado,  **a menos que**  utilizemos o comando  `docker stop <container>`  manualmente.-   `no`  : define que o container não reiniciará automaticamente (Padrão);
-   `on-failure`: define que o container será reiniciado caso ocorra alguma falha apontada pelo  `exit code`, diferente de zero;
-   `always`: especifica que sempre que o serviço parar, seja por um falha ou porque ele simplesmente finalizou sua execução, ele deverá ser reiniciado;
-   `unless-stopped`: define que o container sempre será reiniciado,  **a menos que**  utilizemos o comando  `docker stop <container>`  manualmente.

#### Usando Variáveis de Ambiente

>É possível criar e usar  **variáveis de ambiente**  dentro dos containers. Podemos até especificar para o  _Compose_  utilizar o conteúdo de variáveis de ambiente do nosso próprio computador! O nome da chave que utilizamos é  `environment`. Com esta chave, conseguimos configurar as variáveis de ambiente em nossos serviços do  _Compose_.

>[Mais informações sobre variáveis de ambiente](https://bit.ly/3nNwsXM)

#### Dependência entre Serviços
>Uma configuração importante para garantir a ordem de inicialização e encerramento dos nossos serviços é a chave `depends_on`. Com esta chave, conseguimos criar **dependências entre os serviços**! 🤨

#### Subindo todos os serviços
>Chamamos o ato de executar todos os serviços do  _Compose_  de  **subir**. Para subir todos os serviços utilizamos o comando  `docker-compose up`  no terminal.

⚠️ Lembre-se que o arquivo  `docker-compose.yaml`  deve estar na mesma pasta da execução deste comando.

#### Verificando o status dos serviços

>Agora precisamos visualizar o **status** dos nossos serviços. Faremos isso usando o comando `docker-compose ps`. Este comando traz um resumo do nome interno dos containers, se os containers estão saudáveis e se as portas foram mapeadas corretamente.
ex:
```bash
luccarendall: pasta-do-exercicio$ docker-compose ps
             Name                           Command               State                    Ports                  
------------------------------------------------------------------------------------------------------------------
aula-docker-compose_backend_1    npm start                        Up      0.0.0.0:3001->3001/tcp,:::3001->3001/tcp
aula-docker-compose_database_1   docker-entrypoint.sh mongod      Up      27017/tcp                               
aula-docker-compose_frontend_1   npm start                        Up      0.0.0.0:3000->3000/tcp,:::3000->3000/tcp

```

>_Vamos acessar o nosso front-end e verificar se deu tudo certo?_  🤔
Para isso, abra um navegador web e acesse o endereço  `http://localhost:3000`.

#### Reconstruindo a Imagem Docker
>É comum fazer várias alterações em nosso código durante a fase de desenvolvimento. Algumas dessas alterações nos obrigam a **reconstruir** a Imagem Docker, ou seja, precisamos _forçar_ a execução do `docker build` novamente.
