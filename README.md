# Especificação Técnica & Planejamento SDLC
> **Projeto:** CineList — Catálogo & Gerenciador Pessoal de Filmes  
> **Disciplina:** Engenharia de Software / SDLC  
> **Autor:** Gabriel Feliciano de Oliveira Costa  

---

## 1. Termo de Abertura do Projeto (Project Charter)

* **Título do Projeto:** CineList
* **Problema Real:** Amantes de cinema frequentemente esquecem recomendações de filmes, não lembram quais títulos já assistiram e têm dificuldade em manter uma lista organizada por gênero e avaliação pessoal em um único lugar simples e acessível.
* **Proposta de Valor:** Uma plataforma centralizada e intuitiva para organizar e catalogar filmes assistidos e a assistir, permitindo classificar com notas e organizar por categorias de forma ágil.
* **Escopo In (Dentro do Escopo):**
  * Cadastro de filmes com título, gênero, ano de lançamento, status (*Assistido* / *Para Assistir*) e nota (1 a 5 estrelas).
  * Listagem geral de filmes cadastrados.
  * Filtro por gênero ou por status.
  * Exclusão de filmes do acervo.
  * Persistência local no navegador (`LocalStorage`).
* **Escopo Out (Fora do Escopo nesta versão):**
  * Autenticação e cadastro de múltiplos usuários.
  * Integração com APIs externas de dados (ex: TMDB / IMDb).
  * Streaming ou reprodutor de vídeo integrado.

---

## 2. Histórias de Usuário (User Stories)

| ID | Persona | Ação / Funcionalidade | Benefício Concreto |

| **US01** | Como **cinéfilo** | Quero cadastrar um filme informando título, gênero, ano e nota | Para manter um histórico organizado de tudo o que já assisti. |
| **US02** | Como **usuário** | Quero filtrar meus filmes por status (*Assistido* ou *Para Assistir*) | Para escolher rapidamente o próximo filme da minha lista no fim de semana. |
| **US03** | Como **usuário** | Quero excluir um filme da minha lista | Para remover cadastros incorretos ou duplicados. |

---

## 3. Requisitos do Sistema

### Requisitos Funcionais (RF)
- [x] **RF01:** O sistema deve permitir o cadastro de filmes contendo: Título, Gênero, Ano, Status (*Assistido* / *Para Assistir*) e Avaliação (1 a 5).
- [x] **RF02:** O sistema deve listar todos os filmes cadastrados com suas respectivas informações em cards ou tabela.
- [x] **RF03:** O sistema deve permitir filtrar a lista de filmes por Gênero ou Status.
- [x] **RF04:** O sistema deve permitir a remoção/exclusão permanente de um filme catalogado.

### Requisitos Não-Funcionais (RNF)
- [x] **RNF01 (Desempenho):** O tempo de resposta para adição, filtragem ou exclusão de um filme na tela deve ser inferior a 500ms.
- [x] **RNF02 (Persistência):** Os dados do catálogo devem ser salvos no `LocalStorage` do navegador, garantindo a permanência dos dados após recarregar a página.
- [x] **RNF03 (Usabilidade):** A interface deve ser responsiva e adaptável a telas de smartphones, tablets e desktops.

---

## 4. Caso de Uso Principal & Tratamento de Erros

### Caso de Uso Principal: Cadastrar Novo Filme
1. **Passo 1 (Entrada):** O usuário preenche o formulário com Título (*"Interstellar"*), Gênero (*"Ficção Científica"*), Ano (*"2014"*), seleciona *"Assistido"* e atribui Nota *"5"*. Em seguida, clica em **"Salvar Filme"**.
2. **Passo 2 (Processamento):** O sistema valida os campos obrigatórios (Título e Gênero), gera um ID único, insere o registro na estrutura de dados e atualiza o `LocalStorage`.
3. **Passo 3 (Retorno):** O sistema limpa o formulário, exibe uma mensagem de sucesso e insere dinamicamente o card do novo filme na interface.

### Fluxo de Exceção: Entrada Inválida
* **Cenário:** O usuário clica em **"Salvar Filme"** deixando o campo Título em branco ou digitando um ano inválido.
* **Tratamento:** O sistema interrompe o cadastro, destaca os campos inválidos em vermelho e exibe a mensagem de aviso: *"Por favor, preencha o título do filme e insira um ano válido."*

---

## 5. Arquitetura & Stack Tecnológica

* **Interface / Frontend:** HTML5, CSS3 (com Flexbox/Grid) e JavaScript puro (ES6+ / DOM Scripting).
* **Lógica / Backend:** Client-side execution (executado diretamente no navegador via JavaScript).
* **Armazenamento:** `LocalStorage` (armazenamento nativo chave-valor no navegador).
* **Justificativa da Escolha:** A combinação de tecnologias web nativas é extremamente leve, elimina a necessidade de infraestrutura de servidor complexa para este escopo inicial e garante alta performance e entrega ágil.

---

## 6. Critérios de Aceite & Definição de Pronto (Definition of Done)

O projeto será considerado **Pronto (Done)** quando atender aos seguintes critérios:
1. Permite **cadastrar, listar, filtrar e remover** filmes sem erros no console do navegador.
2. Mantém os dados salvos após o fechamento ou atualização do navegador (`LocalStorage` funcional).
3. Possui validação de formulário impedindo envios com campos obrigatórios vazios.
4. Interface 100% responsiva (mobile e desktop).