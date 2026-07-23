# Casos de Teste — Sistema de Gestão da Escola Dominical

> Testes manuais organizados por módulo. Cada caso descreve a pré-condição, os passos, o resultado esperado e o resultado obtido.

---

## Módulo 1 — Classes

---

### CT-01 — Criar nova classe com dados válidos

**Pré-condição:** Sistema iniciado, aba Classes aberta.

**Passos:**
1. Clicar em "+ Nova Classe"
2. Informar o nome "Jovens"
3. Selecionar o emoji 🌟
4. Selecionar a cor azul
5. Clicar em "Salvar Classe"

**Resultado esperado:** Classe "Jovens" aparece na lista com o emoji e a cor selecionados.

**Status:** ⬜ Não executado

---

### CT-02 — Tentar criar classe sem informar nome

**Pré-condição:** Modal de nova classe aberto.

**Passos:**
1. Deixar o campo nome vazio
2. Clicar em "Salvar Classe"

**Resultado esperado:** Sistema não salva e exibe alerta de campo obrigatório.

**Status:** ⬜ Não executado

---

### CT-03 — Renomear classe existente

**Pré-condição:** Ao menos uma classe cadastrada.

**Passos:**
1. Clicar em "✏️ Renomear" na classe desejada
2. Alterar o nome para "Adolescentes"
3. Clicar em "Salvar Classe"

**Resultado esperado:** Nome da classe atualizado na lista e em todas as telas do sistema.

**Status:** ⬜ Não executado

---

### CT-04 — Excluir classe sem alunos e sem chamadas

**Pré-condição:** Classe cadastrada sem alunos ativos e sem chamadas.

**Passos:**
1. Clicar em "🗑️ Excluir" na classe
2. Confirmar a exclusão

**Resultado esperado:** Classe removida da lista.

**Status:** ⬜ Não executado

---

### CT-05 — Tentar excluir classe com alunos ativos

**Pré-condição:** Classe com ao menos um aluno ativo.

**Passos:**
1. Tentar clicar em "🗑️ Excluir"

**Resultado esperado:** Botão exibe mensagem "Possui alunos ativos". Exclusão não é permitida.

**Status:** ⬜ Não executado

---

## Módulo 2 — Alunos

---

### CT-06 — Cadastrar novo aluno

**Pré-condição:** Ao menos uma classe cadastrada.

**Passos:**
1. Ir para a aba "Alunos"
2. Clicar em "+ Novo Aluno"
3. Informar o nome "Maria Souza"
4. Selecionar uma classe
5. Clicar em "Salvar Aluno"

**Resultado esperado:** Aluno "Maria Souza" aparece na lista com status "Ativo" e vinculado à classe selecionada.

**Status:** ⬜ Não executado

---

### CT-07 — Inativar aluno

**Pré-condição:** Aluno com status "Ativo" cadastrado.

**Passos:**
1. Clicar em "🚫 Inativar" no aluno desejado

**Resultado esperado:** Status do aluno muda para "Inativo". Aluno não aparece na chamada.

**Status:** ⬜ Não executado

---

### CT-08 — Excluir aluno com histórico de frequência

**Pré-condição:** Aluno com registros de frequência.

**Passos:**
1. Clicar em "🗑️" no aluno
2. Confirmar a exclusão

**Resultado esperado:** Sistema exibe aviso com a quantidade de registros que serão apagados. Após confirmação, aluno e registros são removidos.

**Status:** ⬜ Não executado

---

### CT-09 — Pesquisar aluno por nome

**Pré-condição:** Dois ou mais alunos cadastrados.

**Passos:**
1. Digitar parte do nome no campo de busca

**Resultado esperado:** Lista filtrada exibe apenas alunos cujo nome contém o texto digitado.

**Status:** ⬜ Não executado

---

## Módulo 3 — Chamada

---

### CT-10 — Registrar chamada completa

**Pré-condição:** Classe com alunos ativos cadastrados.

**Passos:**
1. Ir para a aba "Chamada"
2. Selecionar a data e a classe
3. Clicar em "▶ Carregar Alunos"
4. Definir o status de cada aluno
5. Informar a oferta e o número de visitantes
6. Clicar em "💾 Salvar Chamada"

**Resultado esperado:** Chamada salva com sucesso. Mensagem de confirmação exibida.

**Status:** ⬜ Não executado

---

### CT-11 — Tentar salvar chamada com aluno sem situação

**Pré-condição:** Chamada carregada com ao menos um aluno sem status definido.

**Passos:**
1. Definir status de todos os alunos exceto um
2. Clicar em "💾 Salvar Chamada"

**Resultado esperado:** Sistema exibe alerta identificando o(s) aluno(s) pendente(s). Chamada não é salva.

**Status:** ⬜ Não executado

---

### CT-12 — Tentar registrar chamada duplicada

**Pré-condição:** Chamada já registrada para a classe "Jovens" na data 06/07/2026.

**Passos:**
1. Selecionar a mesma data e a mesma classe
2. Clicar em "▶ Carregar Alunos"

**Resultado esperado:** Sistema entra em modo de edição e exibe aviso de chamada já registrada.

**Status:** ⬜ Não executado

---

### CT-13 — Verificar cálculo de pontuação automática

**Pré-condição:** Chamada carregada.

**Passos:**
1. Localizar um aluno na lista
2. Selecionar status PRESENTE para um aluno (base: 15 pts)
3. Ativar bônus HARPA (+5 pts)
4. Selecionar 2 perguntas respondidas (+10 pts)

**Resultado esperado:** Placar do aluno exibe 🎯 30 pts em tempo real, sem necessidade de salvar.

**Status:** ⬜ Não executado

---

### CT-14 — Verificar que bônus são desabilitados em FALTA

**Pré-condição:** Chamada carregada.

**Passos:**
1. Selecionar status FALTA para um aluno
2. Tentar clicar nos bônus (HARPA, PROF., MÚSICO)

**Resultado esperado:** Área de bônus aparece desabilitada (opaca). Pontuação permanece 0.

**Status:** ⬜ Não executado

---

## Módulo 4 — Indicadores

---

### CT-15 — Consultar indicadores por data com chamadas registradas

**Pré-condição:** Ao menos uma chamada registrada.

**Passos:**
1. Ir para a aba "Indicadores"
2. Informar a data de uma chamada existente
3. Clicar em "🔍 Consultar"

**Resultado esperado:** Sistema exibe os três cards de destaque (presença, oferta, visitantes) e a tabela detalhada por classe.

**Status:** ⬜ Não executado

---

### CT-16 — Consultar indicadores por data sem chamadas

**Pré-condição:** Nenhuma chamada registrada na data informada.

**Passos:**
1. Informar uma data sem registros
2. Clicar em "🔍 Consultar"

**Resultado esperado:** Sistema exibe mensagem informando que não há chamadas nessa data.

**Status:** ⬜ Não executado

---

## Módulo 5 — Relatórios e Exportação

---

### CT-17 — Exportar relatório de frequência em Excel

**Pré-condição:** Ao menos uma chamada registrada.

**Passos:**
1. Ir para a aba "Relatórios"
2. Clicar em "📥 Frequência"

**Resultado esperado:** Arquivo `.xlsx` baixado com colunas: Data, Classe, Aluno, Situação, Presente, Harpa, Professor, Músico, Perguntas, Pontuação.

**Status:** ⬜ Não executado

---

### CT-18 — Filtrar relatório por mês e classe

**Pré-condição:** Chamadas registradas em meses diferentes.

**Passos:**
1. Selecionar um mês no filtro
2. Selecionar uma classe no filtro
3. Verificar os registros exibidos

**Resultado esperado:** Apenas registros do mês e classe selecionados são exibidos.

**Status:** ⬜ Não executado

---

### CT-19 — Visualizar Top 3 Trimestral

**Pré-condição:** Ao menos três alunos com registros de frequência e pontuação.

**Passos:**
1. Ir para a aba "Relatórios"
2. Clicar na aba "🏆 Top 3 Trimestral"

**Resultado esperado:** Pódio exibido com os 3 alunos de maior presença e os 3 de maior pontuação no período filtrado.

**Status:** ⬜ Não executado

---

## Módulo 6 — Backup e Encerramento

---

### CT-20 — Exportar e reimportar backup

**Pré-condição:** Sistema com dados cadastrados.

**Passos:**
1. Clicar em "💾 Exportar Backup" na tela Início
2. Clicar em "🗑️ Zerar Classes" para limpar os dados
3. Clicar em "📂 Importar Backup" e selecionar o arquivo exportado

**Resultado esperado:** Todos os dados são restaurados exatamente como estavam antes da limpeza.

**Status:** ⬜ Não executado

---

### CT-21 — Encerrar trimestre

**Pré-condição:** Chamadas registradas no sistema.

**Passos:**
1. Clicar em "🔚 Encerrar Trimestre" na tela Início
2. Confirmar a operação

**Resultado esperado:** Arquivo de backup exportado automaticamente. Chamadas e frequências removidas. Alunos e classes mantidos.

**Status:** ⬜ Não executado

---

## Legenda de Status

| Ícone | Significado |
|---|---|
| ⬜ Não executado | Teste ainda não foi realizado |
| ✅ Passou | Comportamento conforme esperado |
| ❌ Falhou | Comportamento diverge do esperado |
| ⚠️ Parcial | Passou com ressalvas |
