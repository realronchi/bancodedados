* Auditoria serve para fins de segunrança e problemas com o banco de dados, por exemplo sumindo registro em uma tabela;

* Usuário e senha do sistema: ORACLE/ORACLE;

* Adicionar um usuário a uma tablespace: CREATE USER aaron IDENTIFIED BY soccer DEFAULT TABLESPACE data TEMPORARY TABLESPACE temp QUOTA 15M ON data QUOTA 10M ON users PASSWORD EXPIRE;

* Alterar a cota do usuário: ALTER USER aaron QUOTA 0 ON USERS;

* Deletar usuário e seus objeto: DROP USER aaron CASCADE;

*  Verificar QUOTAS de um usuário: SELECT tablespace_name, sum(bytes)/1024 Quota FROM dba_ts_quotas WHERE username = 'AARON' group by tablespace_name;

* Adicionar privilégios: GRANT CREATE SESSION TO aaron WITH ADMIN OPTIONS;

* Deletar privilégios: REVOKE CREATE TABLE FROM aaron;

---------------------

* Tablespace é: ÁREA/ESTRUTURA LÓGICA. PARA CLASSIFICAR E ORGANIZAR O BANCO DE DADOS. GAVETA.

* Alterar tablespace para read only: ALTER TABLESPACE NOME_DA_TABLESPACE READ ONLY;

* Criar uma tablespace: CREATE TABLESPACE NOME_DA_TABLESPACE DATA01 DATAFILE '$ORACLE_DATA/DATA01.DBF' SIZE 100M;

* Informações sobre o banco de dados: SHOW SGA;

* Usuário e senha: SYSTEM/MANAGER;

* Arquivo físico em disco: DATA FILE -> DATA01.DBF;

* Visualizar estrutura física: CD $ORACLE_HOME;

* Grava informações das tablespace: DBA_DATA_FILES;

* Tablespace vão se adequar aos databases;

* Segmento: ESTRUTURA LÓGICA DO BANCO DE DADOS;

* Uma tablespace pode conter uma ou mais data files;

* Estrutura física: DATA FILE.

* Estrutura lógica: SEGMENTS, TABLESPACE...;
 
* Verificar os arquivos físicos das tablespaces: SELECT * FROM DBA_DATA_FILES;

* Adicionar novo data file em uma tablespace.: ALTER TABLESPACE DATA01 ADD DATAFILE "$ORACLE_DATA/data01_01.dbf" SIZE 5M;

* Limpar tela: CLEAR SCREEN;

* Logar usuário: SQLPLUS SCOTT/TIGER;

* Substituir palavra sql: C/EMP/DATA01.EMP (Substitui o EMP por DATA01.EMP);

* Parar tablespace: ALTER TABLESPACE DATA01 OFFLINE;

* Iniciar tablespace: ALTER TABLESPACE DATA01 ONLINE;

* Arquivo físico dos data files: CD $ORACLE_DATA;

* Alteração de arquivo físico data file: Altera somente o ponteiro e não cria uma novo data file. Copiar via sistema operacioal.. Mover a tablespace para offline. ALTER TABLESPACE DATA01 RENAME DATAFILE "$ORACLE_DATA/ORACLE1/USERDATA01.DBF" TO "$HOME/ORACLE02/USERDATA01.DBF";

* Excluir tablespece: DROP TABLESPACE DATA01 INCLUDING CONTENTS AND DATAFILES;

* Espaço livres das tablespace: SELECT TABLESPACE_NAME, SUM(BYTES)/1024 FROM DBA_FREE_SPACE GROUP BY TABLESPACE_NAME;

* PCTFREE: ESPECIFICA A PORCENTAGEM DE ESPAÇO PARA CADA BLOCO DE DADOS RESERVADO PARA FUTURA ATUALIZAÇÃO DA TABELA A SER CRIADA. Default = 10;

* PCTUSED: ESPECIFICA O PERCENTUAL MINIMO DE ESPAÇO PARA MANUTENÇÃO DOS BLOCOS DE DADOS DA TABELA. A SOMA DO PCTUSED COM O PCTFREE NÃO DEVERÁ PASSAR DE 100. Default = 40;

* INITTRANS: ESPECIFICA O NUMERO INICIAL DE ENTRADA DE TRANSAÇÕES ALOCADAS PARA CAD BLOCO DE DADOS. Intervalo de 1 á 255. Default = 1;

* MAXTRANS: ESPECIFICA O NÚMERO MÁXIMO DE TRANSAÇÕES CONCORRENTES QUE PODERÃO ATUALIZAR O BLOCO DE DADOS DA TABELA. NÃO LIMITE PARA APLICAR EM CONSULTAS. Intervalo enre 1 a 255. Default = 255;

* Alteração concorrente. Liberar recurso: FIFO. PRIMEIRO QUE ENTRA É O PRIMEIRO QUE SAI;

* INITIAL: ESPECIFICA O TAMANHO EM BYTES PARA A TABELA;

* PCTINCREASE: ESPECIFICA O PERCENTUAL DE CADA EXTEND DA TABELA;

* FRAGMENTAÇÃO = PROBLEMA DE PERFORMANCE;

* ANTES DE CRIAR UMA TABELA, É ESTIMADO UM CÁLCULO.

* Create tabela: CREATE TABLE SCOTT.EMPLOYEES(EMPLOYEE_ID NUMBER(6), FISRT_NAME VARCHAR2(20), DATE_TODAY DATE DEFAULT SYSDATE, DEPARTMENT_ID NUMBER(4)) TABLESPACE DATA01;

* Create index: CREATE INDEX SCOOT.EMPLOYES_FIRST_NAME ON SCOTT.EMPLOYES(FIRST_NAME) PCTFREE 30 STORAGE(INITIAL 200K NEXT 200K PCTINCREASE 0 MAXEXTENTS 50) TABLESPACE INDX;
