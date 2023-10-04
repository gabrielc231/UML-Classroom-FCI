<h2><a href= "https://www.mackenzie.br">Universidade Presbiteriana Mackenzie</a></h2>
<h3><a href= "https://www.mackenzie.br/graduacao/sao-paulo-higienopolis/ciencia-da-computacao">Ciência da Computação</a></h3>

<font size="+12"><center>
<h1>Sistema de Presenças</h1>
</center></font>

**Conteúdo**

- [Autores](#autores)
- [Descrição do projeto](#descrição-do-projeto)
- [Análise de requisitos funcionais e não-funcionais](#análise-de-requisitos-funcionais-e-não-funcionais)
    - [Requisitos funcionais](#requisitos-funcionais)
    - [Requisitos não-funcionais](#requisitos-não-funcionais)
- [Diagrama de casos de uso](#diagrama-de-casos-de-uso)
- [Descrição dos casos de uso](#descrição-dos-casos-de-uso)
  - [Caso de Uso: Fazer Login](#caso-de-uso-fazer-login)
  - [Caso de Uso: Alterar Senha](#caso-de-uso-alterar-senha)
  - [Caso de Uso: Realizar Chamada](#caso-de-uso-realizar-chamada)
  - [Caso de Uso: Confirmar os Dados](#caso-de-uso-confirmar-os-dados)
  - [Caso de Uso: Enviar Notificação via Email aos Responsáveis](#caso-de-uso-enviar-notificação-via-email-aos-responsáveis)
- [Diagrama de sequencia](#diagrama-de-sequencia)
- [Diagrama de classes](#diagrama-de-classes)
- [Diagrama de Componentes](#diagrama-de-componentes)
- [Decisões de arquitetura](#decisões-de-arquitetura)
- [Diagrama de implantação](#diagrama-de-implantação)
- [Referências](#referências)

# Autores

* Gabriel Gonzaga Chung

# Descrição do projeto

A tarefa de registrar a presença dos alunos em uma escola ainda é feita de forma analógica. Deste modo, foi analisado a necessidade de criar um sistema para a computação de presença de maneira virtual. Para que assim, se tenha um acesso remoto destes dados e uma facilitação neste processo. Por isso, nesse repositório, será desenvolvido um **Sistema de Presenças**.

# Análise de requisitos funcionais e não-funcionais

### Requisitos funcionais

1. Adicionar ou Remover falta para os alunos que não responderem a chamada de presença.
2. A chamada deve ocorrer todos os dias e em dois momentos (inicio do dia e após o intervalo).
3. Gerar relatórios de faltas agrupados por data, ano letivo, turma, disciplina, professor ou aluno.
4. Notificar os responsáveis via e-mail caso a presença às aulas do aluno, dadas até o momento, estiverem abaixo de 80%.
5. Caso o aluno não comparecer em pelo menos 75% do total de aulas do ano será reprovado.
6. Cada professor deve ter um nome de usuário (username) e uma senha (password) para entrar no sistema.


### Requisitos não-funcionais

1. O sistema deve ser fácil e intuitivo.
2. O sistema deve ser implementado em web: HTML, CSS e JavaScript.
3. O sistema deve utilizar um banco de dados.
4. O sistema deve permitir acessos simultâneos.
5. O sistema deve ser acessível a todos (fonte ajustável, etc).
6. O sistema deve ser acessado de qualquer navegador web, incluindo dispositivos móveis.
7. O sistema deve ser responsivo na web e mobile.
8. Os relatórios gerados devem ser enviados para os responsáveis semestralmente.
9. O nome de usuário de cada professor deve conter ao menos 10 caracteres.
10. Os usuários devem conter um identificador único.
11. A senha de cada professor deve conter no minímo 10 caracteres contendo letras e números.


# Diagrama de casos de uso

![Diagrama de casos e uso](/images/Diagrama%20de%20casos%20e%20uso.png "Diagrama de casos e uso")

# Descrição dos casos de uso

## Caso de Uso: Fazer Login

**Descrição Geral:** Esse caso de uso se trata do professor efetuar o login no sistema.

**Atores:** Professor.

**Pré-condição:** Professor deve receber suas credenciais da diretoria da escola.

**Pós-condição:** O professor consegue acessar o sistema.

**Fluxo Básico (Professor acessa o sistema):**

1. O professor insere suas credenciais (username e senha);
2. O sistema verifica as credenciais no Banco de Dados e autentica o professor;
3. O professor entra no Sistema.


**Fluxo Alternativo (Professor não consegue acessar o sistema):**

1. O professor insere suas credenciais (nome de usuario e senha);
2. O sistema não consegue verificar as credenciais informadas no Banco de Dados (bug ou erro de digitação);
3. O Professor deve executar a ação novamente.  


## Caso de Uso: Alterar Senha

**Descrição Geral:** Esse caso de uso se trata do professor alterar sua senha.

**Atores:** Professor.

**Pré-condição:** O professor deve estar autenticado no sistema.

**Pós-condição:** A senha do professor é alterada no sistema.

**Fluxo Básico (Professor troca de senha):**

1. O professor acessa a opção de alterar senha no sistema;
2. O professor fornece a senha atual e a nova senha;
3. O sistema verifica a senha atual, atualiza a senha e confirma a alteração.


**Fluxo Alternativo (Professor não consegue trocar de senha):**

1. O professor insere senha atual incorreta;
2. O sistema exibe uma mensagem de erro;
3. O Professor deve executar a ação novamente.  


## Caso de Uso: Realizar Chamada

**Descrição Geral:** Esse caso de uso se trata do professor realizar a chamada em uma turma.

**Atores:** Professor.

**Pré-condição:** O professor deve estar conectado no sistema.

**Pós-condição:** A chamada da turma é registrada no Banco de Dados.

**Fluxo Básico (Professor faz a chamada):**

 1. O professor seleciona a turma e a data para a chamada;
 2. O sistema exibe a lista de alunos da turma.
 3. O professor marca o aluno caso este esteja ausente.
 4. O sistema registra as informações de presença/ausência.


**Fluxo Alternativo (Aluno teve imprevisto e chegou após a chamada):**

1. O professor seleciona a turma do aluno e a data;
2. O sistema exibe a lista de alunos da turma, já com os dados salvos da chamada;
3. O professor desmarca a ausência de tal aluno;  
4. O sistema atualiza as informações de presença ou ausência.


**Fluxo Alternativo (Professor marcou algo errado):**

1. O professor seleciona a turma e a data;
2. O sistema exibe a lista de alunos da turma, com a última alteração salva;
3. O professor corrige o que precisa;  
4. O sistema atualiza as informações de presença ou ausência.


## Caso de Uso: Confirmar os Dados

**Descrição Geral:** Esse caso de uso se trata do professor confirmar os dados de presença, fazendo o sistema emitir relatórios relacionados a presença para cada aluno.

**Atores:** Professor.

**Pré-condição:** O professor está logado no sistema e fez a chamada.

**Pós-condição:** Os relatórios são gerados com as informações relacionados a presença de cada aluno.

**Fluxo Básico (Professor confirma dados):**

1. Para confirmar que a chamada foi realizada, professor clica no botão: **Confirmar Dados.** 
2. Quando este botão é pressionado, o sistema gera relatórios de faltas agrupados por data, ano do ensino, turma, professor, disciplina ou aluno.


**Fluxo Alternativo (Professor não conseguiu confirmar dados):**

1. O professor clica no botão: **Confirmar Dados**.
2. O sistema não gera os relatórios por motivos de bug.
3. O professor deve executar a ação novamente.  


## Caso de Uso: Enviar Notificação via Email aos Responsáveis

**Descrição Geral:** Este caso de uso trata do meio pelo qual a escola irá avisar os pais ou responsáveis caso o comparecimento do aluno às aulas, até o momento, esteja abaixo de 80%.

**Atores:** Professor, Responsáveis.

**Pré-condição:** Foram gerados relatórios de presença do aluno.

**Pós-condição:** As notificações são enviadas aos responsáveis.

**Fluxo Básico (Notificação é enviada):**

1. O sistema gera um relatório da taxa de presença do aluno até o momento;
2. O sistema calcula a porcentagem da presença do aluno em relação ao número total de aulas ministradas;
3. Envia a notificação se o resultado obtido for menor que 80%, para que os pais/responsáveis tomem as medidas necessárias.
4. O sistema registra a data e hora do envio da notificação.


**Fluxo Alternativo (Erro no envio da notificação via Email):**

1. Ocorreu um erro durante o envio da notificação por e-mail;
2. O sistema registra o erro;
3. O sistema tenta reenviar a notificação, até obter êxito.  


# Diagrama de sequencia

 <figure>
 <center>
  <img src="../images/Diagrama%20Sequencia.png"   alt="registro de presença" style="width:100%">
  <figcaption>Diagrama de Sequencia de registro de presença.</figcaption>
  </center>
</figure> 

 <figure>
 <center>
  <img src="../images/Diagrama%20Sequencia%202.png"   alt="alteração de senha" style="width:100%">
  <figcaption>Diagrama de Sequencia de alteração de senha.</figcaption>
  </center>
</figure> 


# Diagrama de classes

*&lt;Diagrama de relacionamento entre classes para os seus atributos e operações&gt;*

# Diagrama de Componentes

*&lt;Diagrama para exibir a relação estrutural dos componentes de um sistema de software&gt;*

# Decisões de arquitetura

*&lt;Descrever a infraestrutura escolhida para arquitetura do projeto&gt;*

# Diagrama de implantação

*&lt;Diagrama para exibir o relacionamento de hardware e software no projeto&gt;*

# Referências

*&lt;Lista de referências&gt;*

