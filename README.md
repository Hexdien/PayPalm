# Índice

- [Instalação do PostgreSQL](#instalação-do-postgresql)
- [Criação do Banco de Dados](#criação-do-banco-de-dados)
- [Populando o Banco de Dados](#populando-o-banco-de-dados)
- [Querys de Análise](#Querys-de-Análise)
- [Integrantes do Projeto](#integrantes)

# Guia de Instalação e Utilização do Banco de Dados

Este guia fornece instruções detalhadas sobre como instalar o Sistema de Gerenciamento de Banco de Dados (SGBD) PostgreSQL, criar o banco de dados, popular com dados iniciais e realizar algumas consultas de análise no banco de dados. Certifique-se de seguir as etapas na ordem indicada.

## Instalação do PostgreSQL

1. **Baixe o PostgreSQL**:
   - Visite o site oficial do PostgreSQL em [https://www.postgresql.org/download/](https://www.postgresql.org/download/).
   - Escolha a versão apropriada para o seu sistema operacional e siga as instruções de instalação.

2. **Instale o PostgreSQL**:
   - Siga as instruções do instalador para concluir a instalação.

3. **Configuração do pgAdmin (opcional)**:
   - O pgAdmin é uma interface gráfica popular para o PostgreSQL. Você pode baixá-lo em [https://www.pgadmin.org/download/](https://www.pgadmin.org/download/).
   - Configure o pgAdmin para se conectar ao servidor PostgreSQL instalado.

## Criação do Banco de Dados

4. **Conexão ao PostgreSQL**:
   - Abra um terminal ou o pgAdmin.
   - Conecte-se ao PostgreSQL usando o usuário e senha configurados durante a instalação.

5. **Crie o Banco de Dados**:
   - Execute o seguinte comando SQL para criar um novo banco de dados chamado "PayPalm":
     ```sql
     CREATE DATABASE PayPalm;
     ```

6. **Seleção do Banco de Dados**:
   - Selecione o banco de dados recém-criado clicando com o botão direito do mouse no banco:
   - ![image](https://github.com/Hexdien/PeyPey/assets/130430133/66d2ecf4-5703-4821-8ce8-432cb88c1a44)
   - Em seguida clique em `Query Tool`
   - ![image](https://github.com/Hexdien/PeyPey/assets/130430133/4abaf125-10ad-4977-98d2-2463707fab87)



## Populando o Banco de Dados

7. **Execução dos Arquivos SQL**:
   - Utilize o utilitário `psql` ou a interface gráfica (pgAdmin) para executar os arquivos SQL que contêm as definições das tabelas e dados de exemplo. Certifique-se de manter a ordem dos arquivos para evitar erros de dependência.

   - Execute os arquivos SQL na seguinte ordem:
     1. `create_tables.sql` para criar as tabelas.
     2. `insert_data.sql` para inserir dados de exemplo nas tabelas.

8. **Verificação dos Dados**:
   - Confirme se os dados foram inseridos corretamente verificando algumas entradas nas tabelas.

## Querys de Análise

9. **Realize Consultas SQL**:
   - Utilize o `psql`, pgAdmin ou sua ferramenta SQL favorita para executar consultas de análise no banco de dados. Aqui estão alguns exemplos:

   - Consulta 1: Quantos usuarios brasileiros possuem 500 reais ou mais na conta.
     ```sql
     select nome_completo, saldo, moeda from cadastro
      join usuario using(id_usuario)
      join saldo using(id_usuario)
      where moeda = 'Real' and saldo >= 500;
     ```

   - Consulta 2: Quantos Usuarios com carteira em Real nós temos.
     ```sql
     select moeda,count(moeda) from cadastro
      join usuario using(id_usuario)
      join saldo using(id_usuario)
      where moeda = 'Real'
      group by moeda;
     ```

   - Consulta 3: Somando todos os usuarios com saldo em Real, qual valor total temos.
     ```sql
     select moeda, sum(saldo) from cadastro
         join usuario using(id_usuario)
         join saldo using(id_usuario)
         where moeda = 'Real'
         group by moeda;
     ```

10. **Explore e Analise**:
    - Utilize essas consultas como ponto de partida para a exploração e análise mais aprofundada do banco de dados.

Este guia fornece os passos essenciais para instalar o PostgreSQL, criar o banco de dados, popular com dados de exemplo e realizar consultas iniciais.


## Integrantes
[Hexdien](https://github.com/Hexdien)

[Álvaro Pubel](https://github.com/AlvaroPoubel)

[Tauan Dias](https://github.com/tauan-dias)

[Thayna Seabra](https://github.com/Thaynaseabra)
