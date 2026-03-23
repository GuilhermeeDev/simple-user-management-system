# Documento de desenvolvimento de software

### Regras para desenvolvimento

**1- Para cada Feature (Nova implementação no sistema) deve ser criado uma Branch no Git do projeto.**

    - Toda Feature implementada fora de uma brach sera considerada má prática de desenvolvimento.
    
    - Toda Branch criada deve possuir um nome objetivo, e uma documentação prévia do que foi implementado / modificado.
    Exemplo: 
        Funcao-remover-pessoa
        - Incrementação de uma função recursiva para remover usuarios.
        - A função espera como parametro o id de um usuario (int id).

**2- Todo commit do projeto deve seguir um padrão de boa pratica de desenvolvimento:**

    - Commit de atualização de codigo existente já existente.
        Exemplo: (update) Nome do commit:
            - Conteudo modificado

    - Commit de adição de arquvo e novo código.
        Exemplo: (add) Nome do commit:
            - Conteudo adicionado
    
    - Commit de remoção de conteudo ou de feature.
        Exemplo: (remove) Nome do commit:
            - O que eu removi
            - Porque removi

    - Commit de correção de bug com ou sem base em Issue.
        Exemplo: (bugfix) Nome do commit:
            - Explicação do bug

**3- Toda Feature deve passar por uma bateria de testes antes de ser Mergeado a Main.**
    
    - A bateria de testes deve ser realizada em um período de no mínimo 2 dias, testando todas as novas funcionalidades do sistema.

    - Os testes realizados devem ser documentados, "O que foi testado, Como foi testado, Dados usados no teste, de que maneira foi feito o teste, foi um teste de longa ou curta duração? (considere 5 min um teste de longa duração pq ngm é de ferro tbm rs)

    - O teste deve seguir o modelo abaixo:
        - Método: Requisição HTTP (Postman)  
        - Dados: Nome, email válido e senha  
        - Resultado esperado: Usuário cadastrado com sucesso  
        - Tipo: Curta duração  

---

### Tecnologias de aprendizado
- Java + Spring Boot
- CRUD 
- Pagina de autenticacao
- Encriptacao e verificacao de usuario
- Banco de dados com PostgreSQL
- Memory cache com Redis
- Containerizacao com Docker
- Orquestracao de containeres com docker compose
- Deploy de sistema nivel intermediario

---

### Pipeline do sistema
Area que possui a vista de cima do sistema, oque obteremos como resultado ao final do projeto: 
- CRUD básico de usuários (Spring Boot + PostgreSQL)
- Autenticação (login + senha com hash)
- Painel admin (queries + métricas)
- Cache com Redis
- Dockerizar tudo
- Nginx + balanceamento de carga

#### Tabelas

---

##### Pessoa
- id (PK, unique, autoincrement)
- nome (not null, varchar: 200)
- email (not null, unique, varchar: 200)
- cpf (not null, unique, char: 11)
- data_hora_criacao (not null, timestamp modelo: dd/mm/aa-hh:mm:ss)

##### Manuseador
- id (PK, unique, autoincrement)
- rgm (unique, char: 20)
- senha (not null, varchar: 1000)

---

#### Explicação do sistema
O sistema Simple User System (Sus) é um sistema para gerenciamento de pessoas cadastradas. Onde um "Manuseador" cadastrado e autenticado pode cadastrar pessoas no sistema e verificar dados através do painel de adiminstração. Todos os dados podem ser exportados em formato de relatorio para um arquivo .csv. 

---

## RF / RNF

### RF
1- O Manuseador de usuarios deve se registrar antes de usar o sistema.

    - O Sistema deve verificar se ja existe algum cadastro com esse rmg (registro geral de manuseador).
    
    - Caso não exista, o sistema efetua o cadastro do novo manuseador
    
    - Caso exista o Sistema deve devolver um error com a mensagem "Manuseador com este RGM já cadastrado". 

2- O Manuseador pode cadastrar pessoas no Sistema.   

    - O Sistema verifica se os dados exigidos com Not Null foram respeitados
    
    - Caso os dados estejam de acordo com o esperado, o Sistema cadastra a nova Pessoa

    - Caso não, o sistema deve devolver um error com a mensagem "Dados de entrada de cadastro não respeitados!"

3- O Manueador pode acessar a pagina de adiministração do Sistema. 

    - O Sistema deve ser capaz de exibir as metricas com base nos dados presentes no banco de dados
    
    - Caso o Manuseador clique na opção de gerar relatório

        - O Sistema deve ser capaz de criar e exportar um relatório no formato .csv e contendo todos os dados presentes no banco de dados


4- O Manuseador pode criar, editar e remover Pessoas do Sistema.

### RNF
1- O Sistema deve ser capaz de gerar relatórios com base nos dados presente no banco de dados.

2- O Sistema deve possuir oa minimo 3 telas.

    1. Tela de cadastro / login de Manuseador
    2. Tela de Cadastro de Pessoa no Sistema, possuindo as opções de criar, editar e remover Pessoa.
    3. Tela de observação de dados do banco de dados.

3- O Sistema deve ser capaz de responder a tela desejada em ate 200ms.

4- O Sistema deve possuir um Memory cache (Redis) com a tela de Observação de dados do banco de dados.

5. O Sistema deve ser capaz de possuir um bom desempenho em 2 Cpus e 512 MB de RAM (Somente o sistema, desconsidere Redis, Nginx e Postgresql).