# 🧪 Casos de Teste — Mercado Livre

**Ambiente:** Google Chrome 122 / Windows 11  
**URL:** https://www.mercadolivre.com.br  
**Data de Execução:** Novembro/2023  
**Executado por:** João Vitor

---

## Legenda de Status

| Status | Significado |
|---|---|
| ✅ Passou | Comportamento conforme esperado |
| ❌ Falhou | Comportamento diferente do esperado |
| ⚠️ Parcial | Passou com ressalvas |

---

## CT-01 — Realizar busca por produto

**Status:** ✅ Passou  
**Pré-condições:** Usuário na página inicial do Mercado Livre  
**Referência:** RF-01, RF-03, RF-04

### BDD (Gherkin)
```gherkin
Dado que o usuário está na página inicial
Quando ele digita "Tênis de corrida" no campo de busca
E clica na lupa ou pressiona Enter
Então uma lista de produtos relacionados deve ser exibida
E os produtos devem ser relevantes ao termo pesquisado
```

### Passos de Execução
| # | Ação | Dados de Entrada | Resultado Esperado |
|---|---|---|---|
| 1 | Acessar a URL | https://www.mercadolivre.com.br | Página inicial carrega |
| 2 | Clicar no campo de busca | — | Campo fica ativo |
| 3 | Digitar termo de busca | "Tênis de corrida" | Texto aparece no campo |
| 4 | Clicar na lupa ou pressionar Enter | — | Página de resultados carrega |

**Resultado Obtido:** Lista com mais de 8.000 produtos relacionados exibida corretamente.  
**Evidências:** [📂 Ver evidências](./Evidências/CT-01/) 

---

## CT-02 — Verificar sugestões automáticas na busca

**Status:** ✅ Passou  
**Pré-condições:** Usuário na página inicial  
**Referência:** RF-02

### BDD (Gherkin)
```gherkin
Dado que o usuário está na página inicial
Quando ele clica no campo de busca
E digita "notebook"
Então sugestões automáticas relacionadas ao termo devem aparecer
E as sugestões devem ser exibidas em tempo real durante a digitação
```

### Passos de Execução
| # | Ação | Dados de Entrada | Resultado Esperado |
|---|---|---|---|
| 1 | Clicar no campo de busca | — | Campo fica ativo |
| 2 | Digitar termo | "notebook" | Sugestões aparecem dinamicamente |

**Resultado Obtido:** Sugestões exibidas corretamente em tempo real.  
**Evidências:** [📂 Ver evidências](./Evidências/CT-02/)
---

## CT-03 — Validar filtro por faixa de preço

**Status:** ❌ Falhou — Ver [BUG-002](relatorio-de-bugs.md#bug-002)  
**Pré-condições:** Usuário na página de resultados de busca  
**Referência:** RF-05, RN-02

### BDD (Gherkin)
```gherkin
Dado que o usuário está na página de resultados de "notebook"
Quando ele aplica filtro de preço mínimo R$1.000 e máximo R$2.000
Então somente produtos entre R$1.000 e R$2.000 devem ser exibidos
E nenhum produto fora desta faixa deve aparecer na listagem
```

### Passos de Execução
| # | Ação | Dados de Entrada | Resultado Esperado |
|---|---|---|---|
| 1 | Buscar produto | "notebook" | Página de resultados carrega |
| 2 | Localizar filtro de preço | — | Filtro visível na lateral |
| 3 | Inserir valor mínimo | R$ 1.000 | Campo preenchido |
| 4 | Inserir valor máximo | R$ 2.000 | Campo preenchido |
| 5 | Confirmar filtro | — | Resultados filtrados |

**Resultado Obtido:** Produtos fora da faixa continuaram aparecendo na listagem.  
**Evidências:** `/evidencias/CT-03/`

---

## CT-04 — Ordenar resultados por menor preço

**Status:** ✅ Passou  
**Pré-condições:** Usuário na página de resultados  
**Referência:** RF-06

### BDD (Gherkin)
```gherkin
Dado que o usuário está na página de resultados de "Relógio"
Quando ele clica em "Ordenar por"
E seleciona a opção "Menor preço"
Então os produtos devem ser exibidos em ordem crescente de preço
E o produto mais barato deve aparecer primeiro
```

### Passos de Execução
| # | Ação | Dados de Entrada | Resultado Esperado |
|---|---|---|---|
| 1 | Buscar produto | "Relógio" | Resultados carregam |
| 2 | Clicar em "Ordenar por" | — | Menu de opções aparece |
| 3 | Selecionar "Menor preço" | — | Lista reordenada |

**Resultado Obtido:** Produtos ordenados corretamente do menor para o maior preço.  
**Evidências:** `/evidencias/CT-04/`

---

## CT-05 — Validar informações na página de produto

**Status:** ✅ Passou  
**Pré-condições:** Usuário na página de resultados  
**Referência:** RF-07

### BDD (Gherkin)
```gherkin
Dado que o usuário busca por "fones bluetooth"
Quando ele clica em um produto da listagem
Então a página do produto deve exibir o nome completo
E o preço com desconto e parcelamento
E as fotos do produto
E a descrição e avaliações de compradores
```

### Passos de Execução
| # | Ação | Dados de Entrada | Resultado Esperado |
|---|---|---|---|
| 1 | Buscar | "fones bluetooth" | Resultados exibidos |
| 2 | Clicar em um produto | — | Página do produto abre |
| 3 | Verificar elementos | — | Nome, preço, fotos, descrição e avaliações presentes |

**Resultado Obtido:** Todos os elementos obrigatórios exibidos corretamente.  
**Evidências:** `/evidencias/CT-05/`

---

## CT-06 — Testar galeria de imagens do produto

**Status:** ✅ Passou  
**Pré-condições:** Usuário na página de um produto com múltiplas imagens  
**Referência:** RF-08

### BDD (Gherkin)
```gherkin
Dado que o usuário está na página de um produto
Quando ele clica em uma miniatura diferente da galeria de imagens
Então a imagem principal deve ser atualizada com a imagem selecionada
```

### Passos de Execução
| # | Ação | Dados de Entrada | Resultado Esperado |
|---|---|---|---|
| 1 | Abrir página de produto | Micro-ondas Mondial | Galeria de miniaturas visível |
| 2 | Clicar em miniatura diferente | — | Imagem principal atualiza |

**Resultado Obtido:** Imagem principal atualizada corretamente ao clicar nas miniaturas.  
**Evidências:** `/evidencias/CT-06/`

---

## CT-07 — Adicionar produto ao carrinho

**Status:** ❌ Falhou — Ver [BUG-003](relatorio-de-bugs.md#bug-003)  
**Pré-condições:** Usuário na página de um produto disponível  
**Referência:** RF-09, RN-01

### BDD (Gherkin)
```gherkin
Dado que o usuário está na página de um produto disponível
Quando ele clica no botão "Adicionar ao carrinho"
Então o produto deve ser incluído no carrinho
E o contador de itens no header deve ser atualizado
E uma confirmação visual deve ser exibida
```

### Passos de Execução
| # | Ação | Dados de Entrada | Resultado Esperado |
|---|---|---|---|
| 1 | Abrir página de produto | Produto aleatório | Botão "Adicionar ao carrinho" visível |
| 2 | Clicar em "Adicionar ao carrinho" | — | Item adicionado, contador atualiza |

**Resultado Obtido:** Em alguns produtos o botão não respondeu. Item não adicionado.  
**Evidências:** `/evidencias/CT-07/`

---

## CT-08 — Alterar quantidade no carrinho

**Status:** ✅ Passou  
**Pré-condições:** Carrinho com ao menos um item  
**Referência:** RF-11

### BDD (Gherkin)
```gherkin
Dado que o usuário está no carrinho com um item adicionado
Quando ele clica no botão "+" para aumentar a quantidade
Então a quantidade do item deve aumentar em 1
E o valor total do carrinho deve ser recalculado automaticamente
```

### Passos de Execução
| # | Ação | Dados de Entrada | Resultado Esperado |
|---|---|---|---|
| 1 | Acessar carrinho | — | Item visível com quantidade 1 |
| 2 | Clicar em "+" | — | Quantidade passa para 2 |
| 3 | Verificar total | — | Total recalculado (R$535 → R$1.070) |

**Resultado Obtido:** Quantidade e valor atualizados corretamente.  
**Evidências:** `/evidencias/CT-08/`

---

## CT-09 — Remover produto do carrinho

**Status:** ✅ Passou  
**Pré-condições:** Carrinho com ao menos um item  
**Referência:** RF-12

### BDD (Gherkin)
```gherkin
Dado que o usuário está no carrinho com itens adicionados
Quando ele clica em "Excluir" em um dos itens
Então o produto deve ser removido da lista do carrinho
E o total deve ser recalculado sem o item removido
```

### Passos de Execução
| # | Ação | Dados de Entrada | Resultado Esperado |
|---|---|---|---|
| 1 | Acessar carrinho | — | Itens visíveis |
| 2 | Clicar em "Excluir" | — | Item removido |
| 3 | Verificar carrinho | — | Total atualizado |

**Resultado Obtido:** Item removido e total recalculado corretamente.  
**Evidências:** `/evidencias/CT-09/`

---

## CT-10 — Validar mensagem de erro no login

**Status:** ✅ Passou  
**Pré-condições:** Usuário deslogado na página inicial  
**Referência:** RF-13, RF-14, RF-15

### BDD (Gherkin)
```gherkin
Dado que o usuário não está autenticado
Quando ele clica em "Entre" no header
E insere um e-mail inválido no campo
E clica em "Continuar"
Então uma mensagem de erro deve ser exibida abaixo do campo
E o sistema não deve avançar para a próxima etapa
```

### Passos de Execução
| # | Ação | Dados de Entrada | Resultado Esperado |
|---|---|---|---|
| 1 | Clicar em "Entre" | — | Tela de login exibida |
| 2 | Inserir e-mail inválido | "joao12345678f4qt3523yg23qh" | Campo preenchido |
| 3 | Clicar em "Continuar" | — | Mensagem de erro exibida |

**Resultado Obtido:** Mensagem "Revise o dado digitado." exibida corretamente abaixo do campo.  
**Evidências:** `/evidencias/CT-10/`

---

## 📊 Sumário de Execução

| ID | Título | Status |
|---|---|---|
| CT-01 | Realizar busca por produto | ✅ Passou |
| CT-02 | Verificar sugestões automáticas | ✅ Passou |
| CT-03 | Validar filtro por faixa de preço | ❌ Falhou |
| CT-04 | Ordenar resultados por menor preço | ✅ Passou |
| CT-05 | Validar informações na página de produto | ✅ Passou |
| CT-06 | Testar galeria de imagens | ✅ Passou |
| CT-07 | Adicionar produto ao carrinho | ❌ Falhou |
| CT-08 | Alterar quantidade no carrinho | ✅ Passou |
| CT-09 | Remover produto do carrinho | ✅ Passou |
| CT-10 | Validar mensagem de erro no login | ✅ Passou |

**Total:** 10 casos | ✅ 8 passaram | ❌ 2 falharam
