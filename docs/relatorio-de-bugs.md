# 🐞 Relatório de Bugs — Mercado Livre

**Ambiente:** Google Chrome 122 / Windows 11  
**URL:** https://www.mercadolivre.com.br  
**Data:** Novembro/2023  
**Reportado por:** João Vitor

---

## Sumário

| ID | Título | Severidade | Prioridade | Status |
|---|---|---|---|---|
| BUG-001 | Sugestões de busca não aparecem ao digitar | Média | Média | Aberto |
| BUG-002 | Filtro de preço não funciona corretamente | Alta | Alta | Aberto |
| BUG-003 | Botão "Adicionar ao carrinho" não responde | Alta | Alta | Aberto |

---

## BUG-001 — Sugestões de busca não aparecem ao digitar

**Severidade:** Média  
**Prioridade:** Média  
**Status:** Aberto  
**Caso de Teste Relacionado:** CT-02  
**Ambiente:** Chrome 122 / Windows 11  
**URL:** https://www.mercadolivre.com.br

### Descrição
Ao digitar um termo no campo de busca, as sugestões automáticas não são exibidas ou aparecem com atraso inconsistente, impedindo o usuário de se beneficiar do recurso de autocompletar.

### Passos para Reproduzir
1. Acessar a página inicial do Mercado Livre
2. Clicar no campo de busca
3. Digitar "celular" rapidamente
4. Observar se sugestões aparecem abaixo do campo

### Resultado Esperado
Sugestões automáticas relacionadas ao termo devem aparecer em tempo real durante a digitação.

### Resultado Obtido
Nenhuma sugestão foi exibida. O campo permaneceu sem autocomplete durante a digitação contínua.

### Impacto
Usuário perde eficiência na busca, tendo que digitar o termo completo sem auxílio de sugestões. Prejudica a experiência de navegação e pode reduzir conversão.

### Evidências
📁 `/Evidencia/bugs/BUG-001/`

---

## BUG-002 — Filtro de preço não funciona corretamente

**Severidade:** Alta  
**Prioridade:** Alta  
**Status:** Aberto  
**Caso de Teste Relacionado:** CT-03  
**Ambiente:** Chrome 122 / Windows 11  
**URL:** https://lista.mercadolivre.com.br/notebook

### Descrição
Ao aplicar filtro de faixa de preço na página de resultados, produtos fora da faixa selecionada continuam sendo exibidos. O filtro é aplicado visualmente (tag aparece na tela), mas não reflete corretamente nos resultados.

### Passos para Reproduzir
1. Buscar "notebook" no campo de busca
2. Na página de resultados, localizar o filtro de preço na lateral esquerda
3. Inserir valor mínimo: R$ 1.000
4. Inserir valor máximo: R$ 2.000
5. Confirmar o filtro
6. Analisar os preços dos produtos exibidos

### Resultado Esperado
Apenas produtos com preço entre R$1.000 e R$2.000 devem ser exibidos na listagem.

### Resultado Obtido
Produtos com preços acima de R$2.000 continuaram aparecendo na listagem mesmo após aplicação do filtro.

### Impacto
**Alto.** O filtro de preço é uma das funcionalidades mais utilizadas em e-commerce. Falha direta na jornada de compra, podendo causar frustração e abandono da plataforma.

### Evidências
📁 `/evidencias/bugs/BUG-002/`

> **Nota técnica:** Possível causa — query de filtro não está sendo aplicada corretamente na requisição à API. Recomenda-se validar o parâmetro `PriceRange` na URL gerada após aplicação do filtro.

---

## BUG-003 — Botão "Adicionar ao carrinho" não responde

**Severidade:** Alta  
**Prioridade:** Alta  
**Status:** Aberto  
**Caso de Teste Relacionado:** CT-07  
**Ambiente:** Chrome 122 / Windows 11

### Descrição
Em determinados produtos, o botão "Adicionar ao carrinho" não executa nenhuma ação ao ser clicado. O carrinho permanece inalterado e nenhuma confirmação visual é exibida.

### Passos para Reproduzir
1. Acessar a página de um produto aleatório
2. Verificar se o produto está disponível em estoque
3. Clicar no botão "Adicionar ao carrinho"
4. Observar se o carrinho é atualizado

### Resultado Esperado
O produto deve ser adicionado ao carrinho imediatamente, com confirmação visual e atualização do contador no header.

### Resultado Obtido
Nada acontece ao clicar no botão. O carrinho permanece vazio e nenhuma resposta visual é exibida.

### Impacto
**Crítico para o negócio.** Impede diretamente a conversão de vendas. Usuário não consegue concluir a jornada de compra.

### Evidências
📁 `/evidencias/bugs/BUG-003/`

> **Nota técnica:** Recomenda-se verificar logs do console do navegador (F12) no momento do clique para identificar possíveis erros de JavaScript ou falha na requisição POST ao endpoint de carrinho.

---

## 📝 Observações Gerais

- Todos os testes foram executados em sessão autenticada com conta pessoal
- Os bugs foram identificados durante execução dos casos de teste CT-03 e CT-07
- BUG-002 e BUG-003 têm impacto direto na jornada de compra e devem ser priorizados
- Recomenda-se reexecução dos testes em outros navegadores (Firefox, Edge) para verificar se os bugs são específicos do Chrome
