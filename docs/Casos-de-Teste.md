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

**Status:** ✅ Passou

---

### CT-02 — Tentar criar classe sem informar nome

**Pré-condição:** Modal de nova classe aberto.

**Passos:**
1. Deixar o campo nome vazio
2. Clicar em "Salvar Classe"

**Resultado esperado:** Sistema não salva e exibe alerta de campo obrigatório.

**Status:** ✅ Passou

---

### CT-03 — Renomear classe existente

**Pré-condição:** Ao menos uma classe cadastrada.

**Passos:**
1. Clicar em "✏️ Renomear" na classe desejada
2. Alterar o nome para "Adolescentes"
3. Clicar em "Salvar Classe"

**Resultado esperado:** Nome da classe atualizado na lista e em todas as telas do sistema.

**Status:** ✅ Passou

---

### CT-04 — Excluir classe sem alunos e sem chamadas

**Pré-condição:** Classe cadastrada sem alunos ativos e sem chamadas.

**Passos:**
1. Clicar em "🗑️ Excluir" na classe
2. Confirmar a exclusão

**Resultado esperado:** Classe removida da lista.

**Status:** ✅ Passou

---

### CT-05 — Tentar excluir classe com alunos ativos

**Pré-condição:** Classe com ao menos um aluno ativo.

**Passos:**
1. Verificar o botão de exclusão na classe

**Resultado esperado:** Botão exibe mensagem "Possui alunos ativos". Exclusão não é permitida.

**Status:** ✅ Passou

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

**Status:** ✅ Passou

---

### CT-07 — Inativar aluno

**Pré-condição:** Aluno com status "Ativo" cadastrado.

**Passos:**
1. Clicar em "🚫 Inativar" no aluno desejado

**Resultado esperado:** Status do aluno muda para "Inativo". Aluno não aparece na chamada. Histórico de frequência é preservado.

**Status:** ✅ Passou

---

### CT-08 — Excluir aluno com histórico de frequência

**Pré-condição:** Aluno com registros de frequência.

**Passos:**
1. Clicar em "🗑️" no aluno
2. Confirmar a exclusão

**Resultado esperado:** Sistema exibe aviso com a quantidade de registros que serão apagados. Após confirmação, aluno e registros são removidos permanentemente.

**Status:** ✅ Passou

---

### CT-09 — Pesquisar aluno por nome

**Pré-condição:** Dois ou mais alunos cadastrados.

**Passos:**
1. Digitar parte do nome no campo de busca

**Resultado esperado:** Lista filtrada exibe apenas alunos cujo nome contém o texto digitado.

**Status:** ✅ Passou

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

**Status:** ✅ Passou

---

### CT-11 — Tentar salvar chamada com aluno sem situação

**Pré-condição:** Chamada carregada com ao menos um aluno sem status definido.

**Passos:**
1. Definir status de todos os alunos exceto um
2. Clicar em "💾 Salvar Chamada"

**Resultado esperado:** Sistema exibe alerta identificando o(s) aluno(s) pendente(s). Chamada não é salva.

**Status:** ✅ Passou

---

### CT-12 — Tentar registrar chamada duplicada

**Pré-condição:** Chamada já registrada para a classe "Jovens" na data 06/07/2026.

**Passos:**
1. Selecionar a mesma data e a mesma classe
2. Clicar em "▶ Carregar Alunos"

**Resultado esperado:** Sistema entra em modo de edição e exibe aviso de chamada já registrada.

**Status:** ✅ Passou

---

### CT-13 — Verificar cálculo de pontuação automática

**Pré-condição:** Chamada carregada com ao menos um aluno.

**Passos:**
1. Localizar um aluno na lista
2. Selecionar o status **PRESENTE** → sistema atribui 15 pts base
3. Clicar no botão **2** no seletor de perguntas → sistema adiciona +10 pts (2 × 5)
4. Ativar o bônus **HARPA** → sistema adiciona +5 pts

**Resultado esperado:** O placar do aluno exibe 🎯 **30 pts** em tempo real, sem necessidade de salvar.

**Cálculo:** 15 (PRESENTE) + 10 (2 perguntas) + 5 (HARPA) = 30 pts

**Status:** ✅ Passou

---

### CT-14 — Verificar que bônus são desabilitados em FALTA

**Pré-condição:** Chamada carregada.

**Passos:**
1. Selecionar status FALTA para um aluno
2. Tentar clicar nos bônus (HARPA, PROF., MÚSICO, SUPER)

**Resultado esperado:** Área de bônus aparece desabilitada (opaca). Botão SUPER também desabilitado. Pontuação permanece 0.

**Status:** ✅ Passou

---

### CT-15 — Verificar bônus PERGUNTA SUPER

**Pré-condição:** Chamada carregada com ao menos um aluno.

**Passos:**
1. Selecionar status **PRESENTE** para um aluno → 15 pts base
2. Clicar no botão **⚡ PERGUNTA SUPER**

**Resultado esperado:** Placar exibe 🎯 **30 pts** em tempo real.

**Cálculo:** 15 (PRESENTE) + 15 (SUPER) = 30 pts

**Status:** ⬜ Não executado

---

### CT-15B — Verificar que perguntas são desabilitadas em FALTA

**Pré-condição:** Chamada carregada.

**Passos:**
1. Selecionar status FALTA para um aluno
2. Tentar clicar no seletor de perguntas (botões 0, 1, 2, 3, 4)

**Resultado esperado:** Seletor de perguntas aparece desabilitado (opaco) junto com os bônus. Não é possível selecionar nenhuma pergunta. Pontuação permanece 0.

**Status:** ✅ Passou

---

## Módulo 4 — Indicadores

---

### CT-16 — Consultar indicadores por data com chamadas registradas

**Pré-condição:** Ao menos uma chamada registrada.

**Passos:**
1. Ir para a aba "Indicadores"
2. Informar a data de uma chamada existente
3. Clicar em "🔍 Consultar"

**Resultado esperado:** Sistema exibe os quatro cards de destaque (presença, oferta, visitantes e perguntas respondidas) e a tabela detalhada por classe.

**Status:** ✅ Passou

---

### CT-16B — Verificar card de Maior % de Presença

**Pré-condição:** Ao menos uma chamada registrada na data consultada.

**Passos:**
1. Consultar uma data com chamadas registradas
2. Localizar o card "🏆 Maior % de Presença"

**Resultado esperado:** Card exibe o nome da classe com maior percentual de presença. Abaixo da linha divisória, exibe o total de presentes no dia.

**Status:** ✅ Passou

---

### CT-16C — Verificar card de Maior Oferta

**Pré-condição:** Ao menos uma chamada com oferta registrada na data consultada.

**Passos:**
1. Consultar uma data com chamadas registradas
2. Localizar o card "💰 Maior Oferta"

**Resultado esperado:** Card exibe o nome da classe com maior oferta e o valor arrecadado por ela. Abaixo da linha divisória, exibe o total arrecadado por todas as classes no dia.

**Status:** ✅ Passou

---

### CT-16D — Verificar card de Maior nº de Visitantes

**Pré-condição:** Ao menos uma chamada com visitantes registrados na data consultada.

**Passos:**
1. Consultar uma data com visitantes registrados
2. Localizar o card "🚪 Maior nº de Visitantes"

**Resultado esperado:** Card exibe o nome da classe com maior número de visitantes. Abaixo da linha divisória, exibe o total de visitantes de todas as classes no dia.

**Status:** ✅ Passouo

---

### CT-16E — Verificar card de Mais Perguntas Respondidas

**Pré-condição:** Ao menos uma chamada com perguntas registradas na data consultada.

**Passos:**
1. Consultar uma data com perguntas registradas
2. Localizar o card "📝 Mais Perguntas Respondidas"

**Resultado esperado:** Card exibe o nome da classe com maior número de perguntas respondidas. Abaixo da linha divisória, exibe o total de perguntas de todas as classes no dia.

**Status:** ✅ Passou
---

### CT-16F — Verificar tabela Detalhes por Classe

**Pré-condição:** Ao menos uma chamada registrada na data consultada.

**Passos:**
1. Consultar uma data com chamadas registradas
2. Localizar a tabela "Detalhes por Classe"

**Resultado esperado:** Tabela exibe as colunas Classe, Pres., Alunos, Visit., Oferta e % para cada classe. Classes sem chamada naquela data aparecem com opacidade reduzida.

**Status:** ✅ Passou

---

### CT-16G — Verificar tabela Detalhes por Aluno

**Pré-condição:** Ao menos uma chamada registrada na data consultada.

**Passos:**
1. Consultar uma data com chamadas registradas
2. Localizar a tabela "Detalhes por Aluno"

**Resultado esperado:** Tabela exibe todos os alunos com status, pontuação e bônus (Harpa, Prof., Músico) para aquela data.

**Status:** ✅ Passou

---

### CT-17 — Consultar indicadores por data sem chamadas

**Pré-condição:** Nenhuma chamada registrada na data informada.

**Passos:**
1. Informar uma data sem registros
2. Clicar em "🔍 Consultar"

**Resultado esperado:** Sistema exibe mensagem informando que não há chamadas nessa data.

**Status:** ✅ Passou

---

### CT-18 — Verificar empate no indicador de perguntas

**Pré-condição:** Duas ou mais classes com o mesmo total de perguntas respondidas na mesma data.

**Passos:**
1. Registrar chamadas em duas classes com o mesmo número total de perguntas respondidas
2. Ir para a aba **Indicadores**
3. Consultar a data dessas chamadas

**Resultado esperado:** O card **📝 Mais Perguntas Respondidas** exibe fundo cinza, os nomes das classes empatadas separados por " · " e a palavra "Empate" no subtítulo.

**Status:** ✅ Passou

---

## Módulo 5 — Relatórios e Exportação

---

### CT-19 — Exportar relatório de frequência em Excel

**Pré-condição:** Ao menos uma chamada registrada.

**Passos:**
1. Ir para a aba "Relatórios"
2. Clicar em "📥 Frequência"

**Resultado esperado:** Arquivo `.xlsx` baixado com colunas: Data, Classe, Aluno, Situação, Presente, Perguntas, Super, Harpa, Professor, Músico, Pontuação.

**Status:** ✅ Passou

---

### CT-20 — Filtrar relatório por mês e classe

**Pré-condição:** Chamadas registradas em meses diferentes.

**Passos:**
1. Selecionar um mês no filtro
2. Selecionar uma classe no filtro
3. Verificar os registros exibidos

**Resultado esperado:** Apenas registros do mês e classe selecionados são exibidos.

**Status:** ✅ Passou

---

### CT-21 — Visualizar Top 3 Trimestral

**Pré-condição:** Ao menos três alunos com registros de frequência e pontuação.

**Passos:**
1. Ir para a aba "Relatórios"
2. Clicar na aba "🏆 Top 3 Trimestral"

**Resultado esperado:** Pódio exibido com os 3 alunos de maior presença e os 3 de maior pontuação no período filtrado.

**Status:** ✅ Passou

---

## Módulo 6 — Backup e Encerramento

---

### CT-22 — Exportar e reimportar backup

**Pré-condição:** Sistema com dados cadastrados.

**Passos:**
1. Clicar em "💾 Exportar Backup" na tela Início
2. Clicar em "🗑️ Zerar Classes" para limpar os dados
3. Clicar em "📂 Importar Backup" e selecionar o arquivo exportado

**Resultado esperado:** Todos os dados são restaurados exatamente como estavam antes da limpeza.

**Status:** ✅ Passou

---

### CT-23 — Encerrar trimestre

**Pré-condição:** Chamadas registradas no sistema.

**Passos:**
1. Clicar em "🔚 Encerrar Trimestre" na tela Início
2. Confirmar a operação

**Resultado esperado:** Arquivo de backup exportado automaticamente. Chamadas e frequências removidas. Alunos e classes mantidos.

**Status:** ✅ Passou

---

## Módulo 7 — Gráficos

### CT-24 — Verificar renderização dos gráficos

**Pré-condição:** Ao menos uma chamada registrada.

**Passos:**
1. Ir para a aba "Gráficos"

**Resultado esperado:** Os 6 gráficos são exibidos com dados: Presenças por Classe, Ofertas por Classe, Frequência Mensal, Ofertas Mensais, Ranking de Presença e Ranking de Pontuação.

**Status:** ✅ Passou

---

### CT-25 — Verificar ranking de presença

**Pré-condição:** Ao menos 3 alunos com presenças registradas.

**Passos:**
1. Ir para a aba "Gráficos"
2. Localizar o gráfico "🏅 Ranking de Presença — Top 15 Alunos"

**Resultado esperado:** Gráfico exibe os alunos ordenados por número de presenças, do maior para o menor, limitado a 15 alunos.

**Status:** ✅ Passou

---

### CT-26 — Verificar ranking de pontuação

**Pré-condição:** Ao menos 3 alunos com pontuação registrada.

**Passos:**
1. Ir para a aba "Gráficos"
2. Localizar o gráfico "⭐ Ranking de Pontuação — Top 15 Alunos"

**Resultado esperado:** Gráfico exibe os alunos ordenados por pontuação total acumulada, do maior para o menor, limitado a 15 alunos.

**Status:** ✅ Passou

---

## Legenda de Status

| Ícone | Significado |
|---|---|
| ⬜ Não executado | Teste ainda não foi realizado |
| ✅ Passou | Comportamento conforme esperado |
| ❌ Falhou | Comportamento diverge do esperado |
| ⚠️ Parcial | Passou com ressalvas |
