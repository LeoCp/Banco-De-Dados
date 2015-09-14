# Banco De Dados
<img src="http://images.franchiseherald.com/data/images/full/6120/oracle-logo.png"/>
## Linguagem Sql:
### Introdução:
• A <strong>linguagem de consulta estruturada(SQL)</strong> surgiu em meados da decada de 70 sendo seu principal foco ser uma  linguagem que adapta-se ao modelo relacional. Seu sucesso foi tão grande que a ANSI (American National Standarts Institute),  padronizou as implementações da linguagem, hoje a maior parte de BD’s seguem criteriosamente esta padronização, podendo ter algumas variações.
### Tipo de dados:
<img src="https://uploaddeimagens.com.br/images/000/505/114/full/tipo.png?1441984126"/><br>
<strong>• CHAR(COMPRIMENTO):</strong> É um tipo de dado de comprimento fixo. Se você definir uma coluna da tabela como CHAR(10) e armazenar um caractere apenas ele vai armazenar mais nove espaços em branco.<br>
<strong>• NCHAR(COMPRIMENTO):</strong>
### Integridade de dados:
### Intruções Sql:
A linguagem SQL é dividida em <STRONG>subconjuntos</STRONG> de acordo com as operações que queremos efetuar sobre um banco de dados.
#### Linguagem de definição de dados (DDL):
• É usada para definir estruturas de dados ou esquemas.<br>
• Podemos colocar restrições para limitar o tipo de dados a introduzir. Essas tais restrições podem ser declaradas quando  fizermos a instrução CREATE TABLE ou ALTER TABLE que são comandos DDL que cria e altera uma tabela. Alguns tipos comuns de restrições(CONSTRAINT) incluem o seguinte:<br>
<strong>- Not null</strong><br> 
<strong>- Default</strong><br> 
<strong>- Unique</strong><br> 
<strong>- Check</strong> <br> 
<strong>- Primary Key</strong> <br> 
<strong>- Foreign Key </strong>
##### CREATE:</p>
O comando CREATE é usado para criar objetos, como table,view,user..<br><br>
 <strong>+ create table:</strong><br>
Comando para criar uma tabela

```
CREATE TABLE <NOME_DA_TABELA> (
<NOME_DA_COLUNA> <TIPO_DO_DADO> <NOT NULL> <UNIQUE> <DEFAULT VALOR>,
CONSTRAINT <NOME> CHECK(<CONDIÇÃO>),
CONSTRAINT <NOME> UNIQUE (<NOME_DA_COLUNA>),
CONSTRAINT <NOME> PRIMARY KEY (<NOME_DA_PRIMARY_KEY>),
CONSTRAINT <NOME> FOREIGN KEY (<NOME_DA_FOREIGN_KEY>) REFERENCES <NOME_DA_TABELA>(<NOME_DA_COLUNA>)
);
```

Exemplo:
<br>
```
CREATE TABLE Empregado (
idEmpregado INT NOT NULL,
Nome VARCHAR2(50),
idSetor INT,
Cpf INT,
Salario INT,
Endereco VARCHAR2(50),
CONSTRAINT Empregado_un UNIQUE(Cpf),
CONSTRAINT Empregado_ck CHECK(Salario >= 1000),
CONSTRAINT Empregado_pk PRIMARY KEY (idEmpregado),
CONSTRAINT Emp_REF_Set FOREIGN KEY (idSetor) REFERENCES Setor(idSetor)
);
```
<br>
Pode-se acrescentar definições das ações que deverão ser executadas em caso de atualização(ON UPDATE)
ou remoção(ON DELETE) de linhas da tabela. Se a Tabela2 tem chave estrangeira para Tabela1. 
<br><br>
<strong>+ on delete:</STRONG>
```
FOREIGN KEY (<NOME_DA_COLUNA>) REFERENCES <NOME_DA_TABELA>(<NOME_DA_COLUNA>) ON DELETE <NOME_DA_REGRA> 
```
<strong>- restrict:</strong> Se houver uma tentativa de remover uma linha da Tabela1 falhará se alguma linha em Tabela2 combina com a chave.
<br>
<strong>- cascade:</strong> Na remoção de uma linha da Tabela1 implica em remoção de todas as linhas da Tabela2 que combina com a Tabela1.
<br>
<strong>- set null:</strong> Na remoção da Tabela1 implica em colocar NULL em todas os atributos de chave estrangeira de cada linha da Tabela2 que combina.
<br>
<strong>- set default:</strong> Na remoção da linha da Tabela1 implica em colocar valores DEFAULT nos atributos da chave estrangeira de cada linha da Tabela2 que combina.
<br><br>
<strong>+ on update:</STRONG>
```
FOREIGN KEY (<NOME_DA_COLUNA>) REFERENCES <NOME_DA_TABELA>(<NOME_DA_COLUNA>) ON UPDATE <NOME_DA_REGRA> 
```
<strong>- restrict:</strong> O update falhará se um atributo da Tabela1 se existir linhas da Tabela2 que combinam.
<br>
<strong>- cascade:</strong> Fazendo o update do atributo da Tabela1 implica que linhas que combinam com a Tabela2 seram atualizadas. 
<br>
<strong>- set null:</strong>Quando fizer o update da Tabela1 implica que valores da chave estrangeira na Tabela2 que combinam seram NULL
<br>
<strong>- set default:</strong> No update da Tabela1 implica que valores de chave estrangeira da Tabela2 nas linhas que combinam teram valores default aplicados.
<br><br>

##### Alter:  
##### Truncate: 
##### Comment: 
##### Rename: 

#### Linguagem de manipulação de dados(DML):
#### Linguagem de controle de dados (DCL):
#### Linguagem de consulta de dados (DQL):
#### Linguagem de tansação de dados (DTL):

## Oracle BDA:
### Servidor Oracle:
<img src="http://s13.postimg.org/4loc923af/serv.png"/><br>
O servidor oracle é o nome que a Oracle deu para seu SGBD, sendo que ele possui uma <strong>Instancia</strong> e um <strong> banco de dados oracle </strong>, ou <strong>camanda lógia</strong> e <strong>camada física</strong>.<br>
<strong>Camada física</strong> é composta de aqruivos armazenados em disco.<br>
<strong>Camada lógica</strong> mapeia dados para a memoria física.<br><br>
<img src="http://s27.postimg.org/51s4wm3kz/image.png"/><br><br>
A oracle ultiliza a <strong>memoria física</strong> do servidor para armazenar muitos itens para uma <strong>instancia</strong> do Oracle. A instancia é o nome dado a área de memoria e conjunto de processos que são execultados em um banco de dados sendo resposanvel por apenas um banco de dados.
<br>
### Instância:
A instância é composta de uma grande bloco de memoria alocada em uma area chamada <strong>SGA</strong> juntamente com alguns <strong>processos</strong> que integra a SGA e os arquivos de banco de dados  no disco, quando um banco é inicializado uma SGA é alocada e os processos são inicializados.<br>
Assim sendo um banco de dados é a arte passiva de um servidor oracle, alguns processos e estruturas de memoria são necessarios para acessar os dados e gerenciar o banco de dados.<br><br>
<img src="http://docs.oracle.com/database/121/CNCPT/img/cncpt233.gif">
### SGA (System Global Area):<br>
É um conjunto de estruturas de memória compartilhada, o seu conteúdo é compartilhado para todos os <strong>processos</strong> vinculados à instância Oracle. Dentro da SGA tem dados e controle de informação referentes a sua instancia. Os conjuntos de estruturas de memorias são:
#### Shared Poll:
Na shared Poll temos duas principais areas <strong>Libary Cahe</strong> e a <strong>Data dictionary cache</strong>
##### Libary Cahe:
Oracle representa cada instrução SQL executada em uma área <strong>Shared Sql Area</strong> e uma área de <strong>Private Sql Area</strong>. <br>
- Shared Sql Area: Contém a árvore de análise e plano de execução para uma determinada instrução sql, ela armazena informações sobre as instruções SQL e PL/SQL executadas no banco de dados. Na segunda vez que uma instrução SQL idêntica for executada, pelo mesmo ou por outro usuário, o plano de execução já estará calculado, o que reduz o tempo de execução do comando SQL.<br>
- Private Sql Area: Contém dados como informação e memória de tempo de execução de estruturas de ligação.

##### Data dictionary cache:
É um conjunto de tabelas internas do banco de dados, pertencentes aos schemas SYS e SYSTEM, que contêm os metadados
sobre o banco de dados, suas estruturas e privilégios e as funções dos usuários do banco de dados.Ele armazena um subconjunto das colunas das tabelas do dicionário de dados depois que forem lidas pela primeira vez para o
buffer cache. Os blocos de dados das tabelas do dicionário de dados são sempre usados para ajudar no processamento das consultas dos usuários e de outros comandos DML.

#### Large Poll:
A Large Pool é uma área opcional da SGA, sendo utilizada em transações com mais de um banco de dados envolvidos, disponibilizando grandes blocos de memoria para operações que precisam aloca-las de uma vez.

#### Database Buffer Cache:
Armazena os blocos de dados do disco que foram recentemente lidos para atender um comando SELECT ou que contêm blocos
modificados ou adicionados por uma instrução DML.Cada tamanho de bloco diferente (em casos de bases onde há tablespaces com blocos de tamanhos diferentes) exige um buffer cache próprio.

#### Redo Log Buffer:
Trata-se de uma lista cisrcula, um conjunto de conteúdo é gravado periodicemente passadando pelo Redo Log Buffer e depois para o Redo Log files. Ele registra as transações comitadas, e as não comitadas ficam em uma area de <strong>rollbak</strong>. Ele é responsavel por recuperar informações em casos de falhas, o buffer circular da SGA tem informações sobre as alterações do BD, contendo entradas redo de mudanças  feitas por operações DML e DLL, tendo informações necessarias para reconstruir ou refazer essas mudanças ou de operações internas. 

## Bibliografias:
http://www.devmedia.com.br/entedendo-a-linguagem-sql-parte-i/7775
