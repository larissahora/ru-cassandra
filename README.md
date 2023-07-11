# Projeto Sistema de Gerenciamento de Fila do Restaurante Universitário da UFBA utilizando Apache Cassandra

Este projeto foi desenvolvido para a matéria MATB09 Laboratório de Banco de Dados pelos estudantes Bruno Oliveira e Larissa Hora.

## :hammer_and_wrench: Como instalar o Apache Cassandra

### Pré-requisitos
Instale a última versão do `Java 8` ou `Java 11`.  
Para usar `cqlsh`, instale `Python 3.6+` ou `Python 2.7`.  

Agora, você pode escolher o método mais adequado para instalar o Cassandra clicando [aqui](https://cassandra.apache.org/doc/latest/cassandra/getting_started/installing.html#choosing-an-installation-method).  
Se você usa Mac, recomendamos esse [vídeo](https://www.youtube.com/watch?v=JtpsOFXJUBw).  

## :computer: Criando o ambiente

Faça o download do aquivo restaurante_universitario_schema e da pasta dataset localizado na raíz do github.  
Abra o terminal e em um aba rode o comando `cassandra -f` e em outra aba, rode o comando `cqlsh`. 

### Criando o keyspace e tabelas

Copie e cole individualmente cada comando do arquivo `restaurante_universitario_schema` 
A sessão de copiar dados do csv para as tabelas serve para popular o banco de dados.

:warning: Se encontrar o erro **[Errno 24] Too many open files**, tente aumentar o limite de arquivos abertos do seu sistema ou feche arquivos desnecessários.

### Editando cassandra.yaml

O cassandra vem com algumas opções desabilitadas. O arquivo pode estar em diferentes diretórios dependendo da sua instalação, mas possivelmente estará na pasta `etc/cassandra`.    
Para utilizar Materialized Views, procure pela chave `enable_materialized_views` e coloque como `true`.  
Para conseguir se autenticar, procure pela seção **Authentication** e coloque `authenticator: PasswordAuthenticator` e `authorizer: CassandraAuthorizer`(é possível que essas chaves já existam e você só precise descomentar a linha e alterar o valor).     

Após as modificações, reinicie o cassandra com `cassandra -f`   
E agora precisamos nos autenticar para rodar o cqlsh. O cassandra oferece usuário e senha padrão.  
`cqlsh localhost -u cassandra -p password`  
Pronto, podemos começar a manipular usuários e roles. Confira alguns comandos no arquivo `restaurante_universitario_schema`, mas fique a vontade para explorar a [documentação](https://cassandra.apache.org/doc/latest/cassandra/cql/index.html) do Cassandra. 



