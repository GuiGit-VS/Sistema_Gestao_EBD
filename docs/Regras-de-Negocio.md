#  Regras de Negócio — Sistema de Gestão da Escola Dominical

---

## 1. Classes

**RN-01** — Cada classe deve ter um nome único, um emoji e uma cor de identificação.

**RN-02** — Uma classe só pode ser excluída se não possuir alunos ativos nem chamadas registradas.

**RN-03** — Ao excluir uma classe, todos os alunos inativos vinculados e todas as chamadas e frequências associadas são removidos em cascata.

**RN-04** — O sistema não impõe limite de quantidade de classes.

---

## 2. Alunos

**RN-05** — Cada aluno pertence a exatamente uma classe.

**RN-06** — Um aluno pode ter o status **Ativo** ou **Inativo**. Somente alunos ativos aparecem na chamada.

**RN-07** — Ao excluir um aluno, todos os seus registros de frequência e pontuação são removidos junto.

**RN-08** — O ID de cada aluno é gerado automaticamente pelo sistema (string alfanumérica única).

---

## 3. Chamada

**RN-09** — A chamada é realizada por classe e por data. A combinação **classe + data** deve ser única — não é permitido registrar duas chamadas para a mesma classe no mesmo dia.

**RN-10** — Não é possível salvar uma chamada se:
- A data estiver vazia
- A classe não estiver selecionada
- Nenhum aluno estiver carregado
- Algum aluno estiver sem situação definida

**RN-11** — Se já existir chamada registrada para aquela classe e data, o sistema entra em modo de edição, permitindo atualizar os dados.

**RN-12** — A chamada registra para cada aluno:
- Status de presença
- Bônus obtidos
- Número de perguntas respondidas
- Pontuação calculada automaticamente

---

## 4. Status de Presença

**RN-13** — Existem três status de presença:

| Status | Presença Contabilizada | Pontos Base |
|---|---|---|
| ❌ FALTA | Não | 0 pts |
| ⏰ ATRASADO | Sim | +5 pts |
| ✅ PRESENTE | Sim | +15 pts |

**RN-14** — Os status ATRASADO e PRESENTE são considerados iguais para fins de cálculo de percentual de presença.

---

## 5. Sistema de Pontuação

**RN-15** — A pontuação é individual por aluno e calculada automaticamente — não há campo de entrada manual.

**RN-16** — A pontuação total é composta por:
- **Pontos base** do status de presença
- **Bônus** selecionados (acumuláveis entre si)
- **Perguntas respondidas** (0 a 4 perguntas × 5 pts cada)

**RN-17** — Os bônus disponíveis são:

| Bônus | Condição | Pontos |
|---|---|---|
| 🎵 HARPA | Trouxe harpa para a aula | +5 pts |
| 📖 PROF. | Ministrou a aula | +5 pts |
| 🎸 MÚSICO | Tocou instrumento na EBD | +5 pts |
| ⚡ SUPER | Primeiro a responder a pergunta super | +15 pts |

**RN-18** — Todos os valores de pontuação são múltiplos de 5.

**RN-19** — Se o status for FALTA, os bônus ficam desabilitados e a pontuação é zerada automaticamente.

**RN-20** — A pontuação máxima possível por aula é:

```
15 (PRESENTE) + 20 (4 perguntas) + 5 (HARPA) + 5 (PROF.) + 5 (MÚSICO) + (SUPER) = 65 pts
```

---

## 6. Oferta

**RN-21** — A oferta pertence à classe e à data da chamada — não é individual por aluno.

**RN-22** — O valor da oferta é numérico e pode ser zero.

---

## 7. Visitantes

**RN-23** — Os visitantes são contabilizados por classe e por data da chamada.

**RN-24** — Somente a quantidade de visitantes é registrada — não há campo para nome ou identificação individual.

**RN-25** — O número de visitantes mínimo é zero.

---

## 8. Indicadores

**RN-26** — Os indicadores são calculados por data de consulta, considerando apenas as chamadas registradas naquela data.

**RN-27** — O percentual de presença de uma classe é calculado como:

```
Presentes ÷ Total de alunos ativos da classe × 100
```

**RN-28** — São exibidos três indicadores principais:
- Classe com maior percentual de presença + total de presentes
- Classe com maior oferta + total arrecadado no dia
- Classe com maior número de visitantes + total de visitantes

---

## 9. Relatórios e Ranking

**RN-29** — Os relatórios podem ser filtrados por data exata, mês, ano e classe — individualmente ou em combinação.

**RN-30** — O ranking trimestral considera o período definido pelos filtros aplicados. Para obter o ranking de um trimestre completo, o usuário deve filtrar pelo período correspondente.

---

## 10. Encerramento de Trimestre

**RN-31** — O encerramento de trimestre remove todos os registros de chamadas e frequências do período.

**RN-32** — O cadastro de alunos e classes é preservado após o encerramento.

**RN-33** — Antes de apagar os dados, o sistema exporta automaticamente um arquivo de backup identificado com o número do trimestre e o ano (ex: `backup_2T2026_...json`).

---

## 11. Backup

**RN-34** — O backup exporta em formato JSON os seguintes dados: classes, alunos, chamadas e frequências.

**RN-35** — Ao importar um backup, todos os dados atuais são substituídos pelos dados do arquivo importado.

**RN-36** — O backup é compatível entre dispositivos — pode ser exportado em um tablet e importado em outro.
