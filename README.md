# DESAFIO-QA-BEEDOO-2026

## Sobre o Desafio
Este repositório contém a resolução do desafio técnico para QA, envolvendo a análise e testes do módulo de cadastro e listagem de cursos da aplicação disponibilizada.

**Aplicação testada:** [Beedoo QA Tests](https://creative-sherbet-a51eac.netlify.app/)

## Estrutura do Repositório

📁 DESAFIO-QA-BEEDOO-2026/
├── README.md 
├── Casos de Teste https://docs.google.com/spreadsheets/d/1g-onzWTta2lr0PSszqKvO3kn8o_oDd3tBobMpU6rP7c/edit?usp=sharing
├── Evidências https://drive.google.com/drive/u/0/folders/1WXxtFlpb8wVq-DclMy2_CAVx6nbd0hUr
└── Relatório de Bugs 

---

## 🔍 Análise Inicial da Aplicação

### Objetivo da Aplicação
A aplicação tem como objetivo fornecer uma interface para o gerenciamento de um catálogo de cursos, permitindo o cadastro detalhado e a visualização organizada das informações.

### Funcionalidades Identificadas

#### 1. Módulo de Cadastro de Curso
Formulário completo com os seguintes campos:
- **Nome do curso** (texto)
- **Descrição do curso** (área de texto)
- **Instrutor** (texto)
- **Url da imagem de capa** (texto - link)
- **Data de início** (formato dd/mm/aaaa)
- **Data de fim** (formato dd/mm/aaaa)
- **Número de vagas** (numérico)
- **Tipo de curso** (select com opções como "Presencial" e "Online")
- **Botão "CADASTRAR CURSO"** para submissão

#### 2. Módulo de Listagem de Cursos
Exibe os cursos cadastrados com as informações:
- Tipo de curso 
- Nome do curso
- Descrição
- Datas de início e fim
- Número de vagas
- **Botão "EXCLUIR CURSO"** por item

### Principais Fluxos Disponíveis

| Fluxo | Ação | Descrição |
|-------|------|-----------|
| **Fluxo Principal 1** | Cadastrar curso | Preencher todos os campos e salvar um novo curso |
| **Fluxo Principal 2** | Listar cursos | Visualizar todos os cursos cadastrados |
| **Fluxo Alternativo** | Excluir curso | Remover um curso existente através da listagem |

### Pontos Críticos para Teste

| Categoria | O que testar | Por que é crítico |
|-----------|--------------|-------------------|
| **Validações de campos obrigatórios** | Tentar cadastrar sem preencher cada campo individualmente | Evitar dados inconsistentes |
| **Validação de datas** | Data fim anterior à data início, formato inválido | Lógica de negócio essencial |
| **Validação de vagas** | Número negativo, zero, letras, valor muito alto | Impacta planejamento de turmas |
| **Url da imagem** | URL inválida, formato incorreto | Quebra de layout/experiência |
| **Tipo de curso** | Verificar se as opções disponíveis são salvas corretamente | Classificação dos cursos |
| **Caracteres especiais** | Inserir acentos, emojis, scripts (XSS) | Segurança e internacionalização |
| **Limites de caracteres** | Textos muito longos em nome e descrição | Estouro de layout na listagem |
| **Exclusão de cursos** | Excluir curso e verificar se some da lista | Integridade dos dados |
| **Listagem após cadastro** | Confirmar se todas as informações aparecem corretamente | Consistência do sistema |

---

## 📊 Casos de Teste

Os casos de teste foram documentados em uma planilha do Google Sheets, organizados por módulo e tipo de cenário, abrangendo:

- ✅ **Fluxo principal de cadastro de curso**
- ✅ **Listagem de cursos**
- ✅ **Cenários negativos**
- ✅ **Validações de campos**
- ✅ **Comportamentos inesperados**

**📌 Acesse a planilha completa aqui:** https://docs.google.com/spreadsheets/d/1g-onzWTta2lr0PSszqKvO3kn8o_oDd3tBobMpU6rP7c/edit?usp=sharing

### Estrutura da Planilha
A planilha está organizada com as seguintes colunas:
- ID do teste
- Módulo
- Título do caso de teste
- Pré-condições
- Passos para execução
- Resultado esperado
- Resultado obtido 
- Status 
- Observações

---

## 🖼️ Evidências de Execução

As evidências dos testes realizados (prints dos bugs encontrados) estão disponíveis no Google Drive, organizadas por ID do caso de teste.

**📌 Acesse a pasta de evidências aqui:** https://drive.google.com/drive/folders/1WXxtFlpb8wVq-DclMy2_CAVx6nbd0hUr?usp=drive_link

### Lista de Evidências
| Bug ID | Descrição | Arquivo |
|--------|-----------|---------|
| BUG-001 | Cadastro com todos os campos vazios | `bug001_cadastro_campos_vazios.jpeg` |
| BUG-002 | Cadastro apenas com o nome | `bug002_cadastro_apenas_nome.jpeg` |
| BUG-003 | Cadastro sem preencher nome | `bug003_cadastro_sem_nome.jpeg` |
| BUG-004 | Cadastro sem descrição | `bug004_cadastro_sem_descricao.jpeg` |
| BUG-005 | Cadastro sem instrutor | `bug005_cadastro_sem_instrutor.jpeg` |
| BUG-006 | Cadastro sem data de início | `bug006_cadastro_sem_data_inicio.jpeg` |
| BUG-007 | Cadastro sem data de fim | `bug007_cadastro_sem_data_fim.jpeg` |
| BUG-008 | Cadastro sem número de vagas | `bugs008_cadastro_sem_vagas.jpeg` |
| BUG-009 | Cadastro sem tipo de curso | `bug009_cadastro_sem_tipo.jpeg` |
| BUG-010 | Data fim anterior à data início | `bugs010_data_fim_anterior.jpeg` |
| BUG-011 | Número de vagas negativo | `bugs011_vagas_negativas.jpeg` |
| BUG-012 | Vagas zero | `bugs012_vagas_zero.jpeg` |
| BUG-013 | Nome com 300 caracteres (layout quebrado) | `bugs013_nome_300_caracteres.jpeg` |
| BUG-014 | Exclusão não remove curso da lista | `bugs014_exclusao_nao_remove.jpeg` |

---

🐛 Relatório de Bugs
Durante a execução dos testes, foram encontrados os seguintes bugs:

BUG-001: Sistema permite cadastrar curso sem preencher nenhum campo
Passos: 1. Acessar "Cadastrar curso" 2. Deixar todos os campos em branco 3. Clicar em "CADASTRAR CURSO"

Resultado atual: Curso é cadastrado com todos os campos vazios

Resultado esperado: Sistema deveria exibir mensagens de erro para campos obrigatórios

Severidade: Crítica

BUG-002: Sistema permite cadastrar curso apenas com o nome
Passos: 1. Preencher apenas "Nome do curso" 2. Deixar demais campos vazios 3. Clicar em "CADASTRAR CURSO"

Resultado atual: Curso é cadastrado com informações incompletas

Resultado esperado: Sistema deveria validar todos os campos obrigatórios

Severidade: Alta

BUG-003: Sistema permite cadastrar sem preencher nome
Passos: 1. Preencher todos os campos exceto "Nome do curso" 2. Clicar em "CADASTRAR CURSO"

Resultado atual: Curso é cadastrado sem nome

Resultado esperado: Sistema deveria exigir nome do curso

Severidade: Alta

BUG-004: Sistema permite cadastrar sem descrição
Passos: 1. Preencher todos os campos exceto "Descrição" 2. Clicar em "CADASTRAR CURSO"

Resultado atual: Curso é cadastrado sem descrição

Resultado esperado: Sistema deveria exigir descrição

Severidade: Alta

BUG-005: Sistema permite cadastrar sem instrutor
Passos: 1. Preencher todos os campos exceto "Instrutor" 2. Clicar em "CADASTRAR CURSO"

Resultado atual: Curso é cadastrado sem instrutor

Resultado esperado: Sistema deveria exigir instrutor

Severidade: Alta

BUG-006: Sistema permite cadastrar sem data de início
Passos: 1. Preencher todos os campos exceto "Data de início" 2. Clicar em "CADASTRAR CURSO"

Resultado atual: Curso é cadastrado sem data de início

Resultado esperado: Sistema deveria exigir data de início

Severidade: Alta

BUG-007: Sistema permite cadastrar sem data de fim
Passos: 1. Preencher todos os campos exceto "Data de fim" 2. Clicar em "CADASTRAR CURSO"

Resultado atual: Curso é cadastrado sem data de fim

Resultado esperado: Sistema deveria exigir data de fim

Severidade: Alta

BUG-008: Sistema permite cadastrar sem número de vagas
Passos: 1. Preencher todos os campos exceto "Número de vagas" 2. Clicar em "CADASTRAR CURSO"

Resultado atual: Curso é cadastrado sem número de vagas

Resultado esperado: Sistema deveria exigir número de vagas

Severidade: Alta

BUG-009: Campo "Tipo de curso" não é obrigatório
Passos: 1. Preencher todos os campos 2. Não selecionar "Tipo de curso" 3. Clicar em "CADASTRAR CURSO"

Resultado atual: Curso é cadastrado sem tipo definido

Resultado esperado: Tipo de curso deveria ser obrigatório

Severidade: Média

BUG-010: Sistema aceita data fim anterior à data início
Passos: 1. Preencher "Data início" com 30/06/2026 2. Preencher "Data fim" com 01/04/2026 3. Demais campos preenchidos 4. Clicar em "CADASTRAR CURSO"

Resultado atual: Curso é cadastrado com datas inconsistentes

Resultado esperado: Sistema deveria exibir mensagem "Data fim não pode ser anterior à data início"

Severidade: Alta

BUG-011: Sistema aceita número de vagas negativo
Passos: 1. Preencher "Número de vagas" com -5 2. Demais campos preenchidos 3. Clicar em "CADASTRAR CURSO"

Resultado atual: Curso é cadastrado com -5 vagas

Resultado esperado: Sistema deveria aceitar apenas números positivos

Severidade: Média

BUG-012: Sistema aceita URL inválida
Passos: 1. Preencher "Url da imagem" com "nao-e-uma-url" 2. Demais campos preenchidos 3. Clicar em "CADASTRAR CURSO"

Resultado atual: Sistema aceita texto qualquer no campo URL

Resultado esperado: Sistema deveria validar formato de URL

Severidade: Média

BUG-013: Nome muito longo quebra layout da listagem
Passos: 1. Preencher "Nome do curso" com texto de 300 caracteres 2. Demais campos preenchidos 3. Clicar em "CADASTRAR CURSO" 4. Acessar listagem

Resultado atual: Layout da listagem fica quebrado

Resultado esperado: Sistema deveria truncar ou ajustar o texto

Severidade: Baixa

BUG-014: Exclusão de curso não remove da lista
Passos: 1. Acessar "Listar cursos" 2. Clicar em "EXCLUIR CURSO" em qualquer curso 3. Aguardar mensagem verde

Resultado atual: Mensagem "excluído com sucesso" aparece, mas curso continua na lista

Resultado esperado: Curso deveria sumir da listagem imediatamente

Severidade: Crítica

---

## ⚙️ Ambiente de Testes

| Recurso | Especificação |
|---------|---------------|
| **Navegador** | Chrome |
| **Sistema Operacional** | Windows 10 |
| **Ferramentas** | Google Sheets, Google Drive |

---

## 💡 Uso de Inteligência Artificial

Durante o desafio, utilizei IA como ferramenta de apoio para:

- [x] Estruturar a documentação de forma organizada
- [x] Sugerir cenários de teste complementares
- [x] Revisar a clareza dos artefatos produzidos
- [x] Organizar o relatório de bugs

**Como avaliei as sugestões:**
Todas as sugestões foram analisadas criticamente, adaptadas à realidade da aplicação e validadas manualmente durante a execução dos testes.

---

## 📌 Considerações Finais

A aplicação apresenta **diversos bugs críticos** relacionados à validação de campos obrigatórios, consistência de dados e funcionalidade de exclusão. Recomendações:

- Implementar validações no frontend para campos obrigatórios
- Corrigir a lógica de exclusão de cursos
- Validar formato de datas e números
- Adicionar tratamento para textos muito longos
- Implementar validação de URL

---

**Desenvolvido por Eduardo Mutinelli**  
📅 Março/2026
