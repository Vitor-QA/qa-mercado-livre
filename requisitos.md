# 📋 Documento de Requisitos — Mercado Livre

## 🎯 Objetivo

Definir os requisitos funcionais e não funcionais das principais funcionalidades do Mercado Livre, servindo como base para planejamento e execução dos testes.

---

## 📌 Escopo

Funcionalidades analisadas:

- Busca de produtos
- Página de resultados
- Página de produto
- Carrinho
- Login (validação de interface)

---

## ✅ Requisitos Funcionais

| ID | Descrição |
|---|---|
| RF-01 | Permitir inserção de termos no campo de busca |
| RF-02 | Exibir sugestões automáticas em tempo real durante a digitação |
| RF-03 | Permitir execução da busca via botão ou tecla Enter |
| RF-04 | Exibir lista de produtos relevantes ao termo pesquisado |
| RF-05 | Permitir aplicação de filtros (preço, categoria, etc.) |
| RF-06 | Permitir ordenação dos resultados (menor preço, mais vendidos, etc.) |
| RF-07 | Exibir nome, preço, imagens e descrição na página de produto |
| RF-08 | Permitir navegação entre imagens do produto |
| RF-09 | Permitir adicionar produto ao carrinho |
| RF-10 | Exibir itens adicionados no carrinho com preço e quantidade |
| RF-11 | Permitir alterar quantidade de itens no carrinho |
| RF-12 | Permitir remover itens do carrinho |
| RF-13 | Exibir tela de login ao clicar em "Entre" |
| RF-14 | Validar campos obrigatórios no formulário de login |
| RF-15 | Exibir mensagens de erro para dados inválidos |

---

## ⚙️ Requisitos Não Funcionais

| ID | Descrição |
|---|---|
| RNF-01 | Tempo de resposta das páginas deve ser inferior a 3 segundos |
| RNF-02 | Interface deve ser responsiva em diferentes resoluções |
| RNF-03 | Consistência visual entre páginas do sistema |
| RNF-04 | Textos e elementos devem ter legibilidade adequada |

---

## 📐 Regras de Negócio

| ID | Descrição |
|---|---|
| RN-01 | Produto indisponível não pode ser adicionado ao carrinho |
| RN-02 | Preços devem ser exibidos com duas casas decimais |
| RN-03 | Variações obrigatórias (cor, tamanho) devem ser selecionadas antes de adicionar ao carrinho |

---

## 🔄 Fluxos Principais

### Fluxo 1 — Busca e Navegação
1. Usuário acessa a página inicial
2. Insere termo no campo de busca
3. Executa a busca (botão ou Enter)
4. Visualiza lista de resultados
5. Aplica filtros e ordenação
6. Abre página do produto

### Fluxo 2 — Carrinho
1. Usuário seleciona produto
2. Clica em "Adicionar ao carrinho"
3. Sistema atualiza contador do carrinho
4. Usuário acessa carrinho
5. Altera quantidade ou remove item

### Fluxo 3 — Login (Validação de Erro)
1. Usuário clica em "Entre"
2. Insere dados inválidos no formulário
3. Sistema valida os campos
4. Exibe mensagem de erro adequada
