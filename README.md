# Banco De Dados
<img src="http://images.franchiseherald.com/data/images/full/6120/oracle-logo.png"/>
## Linguagem Sql:
### Introdução:
• A <strong>linguagem de consulta estruturada(SQL)</strong> surgiu em meados da decada de 70 sendo seu principal foco ser uma  linguagem que adapta-se ao modelo relacional. Seu sucesso foi tão grande que a ANSI (American National Standarts Institute),  padronizou as implementações da linguagem, hoje a maior parte de BD’s seguem criteriosamente esta padronização, podendo ter algumas variações.
### Integridade de dados:
### Tipo de dados:
### Intruções Sql:
A linguagem SQL é dividida em <STRONG>subconjuntos</STRONG> de acordo com as operações que queremos efetuar sobre um banco de dados.
#### Linguagem de definição de dados (DDL):
É usada para definir estruturas de dados ou esquemas.Os comandos ultilidados são:
##### Create:
O comando CREATE é usado para criar objetos, como table,view,user..<br><br>
• <strong>CREATE TABLE:</strong><br>
Comando para criar uma tabela

```
CREATE TABLE <NOME_DA_TABELA> (
<NOME_DA_COLUNA> <TIPO_DO_DADO> <NOT NULL> <UNIQUE> <DEFAULT VALOR>,
CHECK(<CONDIÇÃO>),
CONSTRAINT <NOME> PRIMARY KEY (<NOME_DA_PRIMARY_KEY>),
CONSTRAINT <NOME> FOREIGN KEY (<NOME_DA_FOREIGN_KEY>) REFERENCES <NOME_DA_TABELA>(<NOME_DA_COLUNA>)
);
```
<br>
Exemplo:
<br>
```
CREATE TABLE Empregado (
idEmpregado INT NOT NULL,
Nome VARCHAR2(50),
idSetor INT,
Salario INT,
Endereco VARCHAR2(50),
CHECK(Salario >= 1000),
CONSTRAINT Empregado_pk PRIMARY KEY (idEmpregado),
CONSTRAINT Emp_REF_Set FOREIGN KEY (idSetor) REFERENCES Setor(idSetor)
);
```
<br>
Pode-se acrescentar definições das ações que deverão ser executadas em caso de atualização(ON UPDATE)
ou remoção(ON DELETE) de linhas da tabela. Se a Tabela2 tem chave estrangeira para Tabela1. 
<br>
<strong>ON DELETE:</STRONG><br>
```
FOREIGN KEY (<NOME_DA_COLUNA>) REFERENCES <NOME_DA_TABELA>(<NOME_DA_COLUNA>) ON DELETE <NOME_DA_REGRA> 
```
<br>
<strong>Regras:</strong><br>
- RESTRICT: Se houver uma tentativa de remover uma linha da Tabela1 falhará se alguma linha em Tabela2 combina com a chave.
<br>
##### Alter:  
##### Truncate: 
##### Comment: 
##### Rename: 

#### Linguagem de manipulação de dados(DML):
#### Linguagem de controle de dados (DCL):
#### Linguagem de consulta de dados (DQL):
#### Linguagem de tansação de dados (DTL):

## Bibliografias:
http://www.devmedia.com.br/entedendo-a-linguagem-sql-parte-i/7775
