# Melhorias no Processamento de Dados

Este repositório contém um conjunto de melhorias no processamento de dados para um conjunto específico de dados. As seguintes etapas foram realizadas para aprimorar a qualidade e a utilidade dos dados:

1. **Remoção de Colunas de Ligação**: Todas as colunas de ligação foram removidas, garantindo que apenas os dados relevantes para as análises permaneçam.

2. **Correção de Tipos de Dados e Precisão**: Os tipos de dados foram ajustados conforme necessário e foi aplicado um formato de número decimal fixo para os salários.

3. **Tratamento de Valores Nulos no Super_ssn**: Identificamos que o único funcionário com valores nulos em Super_ssn é o head da empresa. Portanto, removemos esse funcionário, garantindo que não haja mais funcionários sem gerente ou departamentos sem funcionários.

4. **Transformação de Número de Horas para Inteiro**: Os números de horas foram convertidos para o tipo de dados inteiro para facilitar análises futuras.

5. **Separação da Coluna Endereço**: A coluna de endereço foi dividida em quatro partes distintas: Número, Rua, Cidade e Estado, para melhorar a granularidade e a acessibilidade dos dados.

6. **Mesclagem de Colunas com Externa Esquerda**: Realizamos uma mesclagem das colunas "employee" e "departament" com o método de mesclagem externa à esquerda, garantindo que todos os dados de funcionários sejam preservados, mesmo que não haja uma correspondência completa com os departamentos.

7. **Remoção de Colunas Não Necessárias**: As colunas Super_ssn e Dno foram removidas, pois não são mais relevantes para as análises.

8. **Concatenação de Nomes de Colaboradores**: Os nomes e sobrenomes dos colaboradores foram concatenados para facilitar a identificação e a referência dos indivíduos nos conjuntos de dados.

9. **Junção de Colaboradores com Seus Respectivos Gerentes**: Utilizamos a seguinte consulta SQL para realizar a junção dos colaboradores com seus respectivos gerentes:
```sql
   SELECT CONCAT(e.Fname, " ", e.Minit, " ", e.Lname) AS Name, d.Dname AS Department 
   FROM employee e
   INNER JOIN department d ON e.Dno = d.Dnumber;
```
**nesse caso foi utilizado o mesclar os departamentos com a localização. A razão pela qual usamos a mesclagem ao invés de simplesmente atribuir os dados de uma tabela à outra é garantir que os dados estejam alinhados 
corretamente e que não haja duplicatas ou perda de informações, pois os mesmo tem um relacionamento entre eles.**

10. **Agrupamento de Dados de Colaboradores por Gerentes**: Por fim, os dados dos colaboradores foram agrupados por seus respectivos gerentes para análises agregadas e uma melhor compreensão da estrutura organizacional.

Essas melhorias foram implementadas para garantir que os dados estejam alinhados corretamente, livre de duplicatas e com informações relevantes para análises eficazes.
