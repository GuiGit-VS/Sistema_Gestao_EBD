
#  Sistema de Gestão — Escola Dominical

### Sistema web desenvolvido para gerenciamento de classes, alunos, frequência e indicadores da Escola Dominical.

---

##  Sobre o Projeto

Este sistema foi desenvolvido para atender uma necessidade real de gerenciamento da Escola Dominical, substituindo controles manuais por uma solução digital simples e de fácil utilização.

A aplicação centraliza informações sobre classes, alunos e frequência, além de fornecer indicadores, relatórios e mecanismos de backup dos dados. Foi projetada para ser utilizada diretamente no tablet pelo secretário da Escola Dominical durante as aulas.

Todo o sistema funciona diretamente no navegador, sem necessidade de servidor ou banco de dados, utilizando o LocalStorage como mecanismo de persistência.

---

##  Objetivos

- Organizar o cadastro das classes
- Gerenciar alunos da Escola Dominical
- Registrar frequência dos alunos
- Acompanhar indicadores por meio de gráficos
- Facilitar a geração de relatórios
- Permitir backup e restauração dos dados
- Eliminar a necessidade de controles manuais

---

##  Principais Funcionalidades

###  Gestão de Classes

- Cadastro de classes com nome, emoji e cor personalizáveis
- Edição e exclusão de classes
- Exclusão em cascata — ao remover uma classe, alunos e chamadas vinculados também são removidos

---

###  Gestão de Alunos

- Cadastro de alunos com associação à classe
- Edição, inativação e exclusão individual
- Pesquisa por nome, classe e status

---

###  Controle de Frequência

- Seleção de data e classe com carregamento automático dos alunos
- Três status de presença por aluno:
  - ❌ **FALTA** — 0 pontos
  - ⏰ **ATRASADO** — +5 pontos (conta como presente nos relatórios)
  - ✅ **PRESENTE** — +15 pontos
- Bônus acumuláveis por aluno (independentes entre si):
  - 🎵 **HARPA** — +5 pontos
  - 📖 **PROF.** — +5 pontos (ministrou a aula)
  - 🎸 **MÚSICO** — +5 pontos (tocou na EBD)
  - ⚡ SUPER — +15 pontos (pergunta super, primeiro a levantar a mão)
- Seletor de perguntas respondidas: 0 a 4 perguntas × 5 pontos cada
- Pontuação calculada e exibida automaticamente em tempo real, sem campos manuais
- Campo de oferta por classe
- Campo de visitantes por chamada com controle +/−
- Validação contra duplicidade de chamada na mesma data

---

###  Recursos Administrativos

- Registro de visitantes por classe e data
- Sistema de pontuação por bônus com cálculo automático
- Encerramento de trimestre com exportação automática de backup e limpeza dos registros do período
- Alunos mantidos após o encerramento do trimestre

---

###  Dashboard

O sistema apresenta indicadores e gráficos dinâmicos, incluindo:

- Presenças totais por classe
- Ofertas totais por classe
- Evolução mensal de frequência
- Evolução mensal de ofertas
- Ranking de presença — Top 15 alunos
- Ranking de pontuação — Top 15 alunos

---

###  Indicadores por Data

Consulta por data com exibição de:

- Classe com maior percentual de presença e total de presentes
- Classe com maior oferta e total arrecadado
- Classe com maior número de visitantes e total de visitantes
- Classe com mais perguntas respondidas (+ total de perguntas) com tratamento de empate
- Tabela detalhada por classe e por aluno

---

###  Relatórios

- Filtros por data, mês, ano e classe
- Abas: Frequência / Ofertas / Por Aluno / 🏆 Top 3 Trimestral
- Exportação para Excel (.xlsx):
  - Relatório de Frequência
  - Relatório de Ofertas
  - Relatório Geral
  - Ranking de Alunos

---

###  Backup

- Exportação completa dos dados em JSON (classes, alunos, chamadas e frequências)
- Importação e restauração a partir do arquivo de backup
- Compatível entre dispositivos — basta importar o arquivo

---

##  Tecnologias Utilizadas

| Tecnologia | Finalidade |
|---|---|
| HTML5 | Estrutura da aplicação |
| CSS3 | Estilização e layout responsivo |
| JavaScript ES6+ | Regras de negócio e manipulação do DOM |
| Bootstrap 5 | Interface responsiva |
| Chart.js | Dashboard e gráficos |
| SheetJS (xlsx) | Exportação para Excel |
| LocalStorage | Persistência dos dados |

---

##  Como executar

Clone o repositório:

```bash
git clone https://github.com/guilherme-r-medeiros/Sistema-Escola-Dominical.git
```

Abra o arquivo no navegador:

```
escola_dominical.html
```

O sistema utiliza Bootstrap, Chart.js e SheetJS carregados via CDN. Nenhuma instalação local é necessária. É necessária conexão com a internet no primeiro acesso para carregamento das dependências.

---

##  Conhecimentos Aplicados

Durante o desenvolvimento deste projeto foram utilizados conhecimentos relacionados a:

- Manipulação do DOM
- Programação em JavaScript
- Estruturação de interfaces responsivas para tablets
- Organização de regras de negócio
- Persistência utilizando LocalStorage
- Manipulação de objetos e coleções
- Geração dinâmica de conteúdo HTML
- Dashboard com gráficos (Chart.js)
- Exportação de arquivos Excel (SheetJS)
- Backup e restauração de dados no front-end

---

##  Regras de Negócio

Algumas regras implementadas na aplicação:

- Cada aluno pertence a uma única classe
- A frequência é registrada individualmente por aluno em cada chamada
- A pontuação é calculada automaticamente com base no status de presença mais os bônus selecionados
- Visitantes são contabilizados por classe e por data
- O encerramento do trimestre apaga chamadas e frequências, mantendo o cadastro de alunos
- O sistema valida duplicidade de chamada — não é possível registrar duas chamadas para a mesma classe na mesma data
- Os indicadores são calculados dinamicamente a partir dos registros realizados

---

##  Desafios do Projeto

Durante o desenvolvimento, alguns desafios precisaram ser solucionados:

- Desenvolver toda a lógica utilizando JavaScript puro, sem frameworks
- Criar um mecanismo confiável de persistência utilizando LocalStorage
- Garantir compatibilidade de IDs entre classes e alunos ao importar backups de dispositivos diferentes
- Implementar backup e restauração completos dos dados
- Desenvolver exportação para Excel com formatação de colunas
- Construir dashboards com Chart.js sem re-renderizações desnecessárias
- Implementar regras de negócio específicas da Escola Dominical
- Manter interface simples e com botões grandes para uso em tablets durante o culto

---

##  Melhorias Futuras

- [ ] Tema escuro
- [ ] Banco de dados relacional
- [ ] API REST
- [ ] Backend em Spring Boot ou Node.js
- [ ] Controle de permissões por perfil de usuário
- [ ] Histórico de alterações por registro
- [ ] Sincronização entre dispositivos via nuvem
- [ ] Testes automatizados
- [ ] Deploy em ambiente cloud

---

##  Contribuições

Sugestões de melhoria e feedbacks são sempre bem-vindos.

Caso identifique algum problema ou tenha alguma ideia para evolução do sistema, fique à vontade para abrir uma [Issue](https://github.com/guilherme-r-medeiros/Sistema-Escola-Dominical/issues).

---

##  Licença

Este projeto está licenciado sob a licença MIT.

---

##  Autor

**Guilherme Rodrigues de Medeiros**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/guilherme-rodrigues-de-medeiros-a03431348)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/guilherme-r-medeiros)

---

