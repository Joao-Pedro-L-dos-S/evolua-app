
# Prova de Conceito  
**Evolua: Sistema de Treinamento Personalizado**

---

## 1. Introdução

Este documento apresenta a Prova de Conceito (PoC) do projeto **Evolua**, uma aplicação web destinada ao acompanhamento de treinos personalizados e à motivação de usuários na prática de atividades físicas.

O objetivo da PoC é demonstrar a viabilidade técnica e funcional do sistema, validando sua arquitetura, fluxo de uso e integração entre frontend e backend. Nesta fase inicial, **não haverá qualquer implementação de Inteligência Artificial**, focando unicamente nas funcionalidades essenciais de planos de treino, acompanhamento de progresso e gamificação básica.

---

## 2. Objetivo da Prova de Conceito

A PoC tem como propósito validar:

- A capacidade do sistema de gerenciar usuários, treinos, progresso e medalhas;  
- A comunicação estável entre frontend (JavaScript vanilla) e backend (Flask);  
- A estrutura inicial que permitirá expansão futura para recursos mais avançados, como planos com IA, vídeos de exercícios e integração mobile.  

Especificamente, a PoC busca:

- Comprovar o fluxo básico de uso do Evolua;  
- Validar a arquitetura modular planejada;  
- Mostrar que o sistema funciona, mesmo com um conjunto reduzido de funcionalidades.

---

## 3. Escopo da PoC

A PoC contemplará apenas as funcionalidades essenciais, alinhadas ao que que realmente será implementado no projeto.  

A versão de prova contemplará os seguintes módulos:

### 3.1 Módulo de Usuário

- Cadastro e autenticação de usuários (sem JWT nesta fase);  
- Edição de informações básicas (nome, idade, objetivo, nível, dias por semana, local de treino);  
- Armazenamento seguro das credenciais (hash de senha).

### 3.2 Módulo de Planos de Treino (sem IA)

Apesar de prever planos automáticos com IA, a PoC usará somente planos pré-definidos, conforme a revisão.

Funcionalidades desta fase:

- Exibição de planos estáticos ou cadastrados manualmente na API;  
- Cada plano contém semanas, sessões e exercícios simples;  
- Seleção de um plano para ativação pelo usuário.

### 3.3 Módulo de Registro de Treinos (Workouts)

- Registro de treinos concluídos (data, duração, notas);  
- Associações com o plano ativo do usuário;  
- Consulta do histórico de treinos anteriormente registrados.

### 3.4 Módulo de Progresso

- Registro manual de peso corporal e medidas;  
- Visualização do histórico por gráficos (Chart.js);  
- Dados provenientes diretamente da API.

### 3.5 Módulo de Gamificação

- Sistema de pontuação simples (ex.: 10 pontos por treino concluído);  
- Conquista automática de medalhas básicas (“Primeiro Treino”, “5 Treinos Concluídos”, etc.);  
- Exibição das medalhas no perfil do usuário.

---

## 4. Arquitetura da Solução

A PoC será desenvolvida em uma arquitetura cliente-servidor, com o backend responsável pelas operações de dados e o frontend pela interação com o usuário.

### 4.1 Backend

- Framework: Flask (Python);  
- Banco: SQLite com SQLAlchemy;  
- Estrutura modular com Blueprints;  
- CORS habilitado.

**Principais rotas da API:**

**Users**  
```
POST /api/users – criar usuário
GET /api/users/<id> – detalhes
PUT /api/users/<id> – atualização
```

**Exercises**  
```
GET /api/exercises
POST /api/exercises
```

**Plans**  
```
GET /api/plans/<id>
POST /api/plans
```

**Workouts**  
```
POST /api/workouts
GET /api/workouts/<user_id>
```

**Progress**  
```
POST /api/progress
GET /api/progress/<user_id>
```

**Medals**  
```
GET /api/medals/<user_id>
POST /api/medals
```

### 4.2 Frontend

- HTML5, CSS3 e JavaScript (sem frameworks);  
- SPA simples com navegação sem recarregar;  
- Requisições via fetch();  
- Charts com Chart.js.

**Características principais:**

- Interface simples e responsiva;  
- Comunicação com o backend via fetch() (requisições AJAX);  
- Uso de Chart.js para exibição de gráficos de progresso;  
- Armazenamento local de sessão (localStorage).

---

## 5. Fluxo de Operação da PoC

1. Usuário se cadastra ou faz login;  
2. Preenche dados essenciais: objetivo, nível, dias por semana;  
3. Sistema exibe planos pré-definidos;  
4. Usuário escolhe um plano ativo;  
5. Usuário registra treinos diários;  
6. Sistema contabiliza pontos e medalhas;  
7. Usuário registra peso e medidas;  
8. Sistema apresenta gráficos com evolução do progresso.

---

## 6. Escopo Fora da PoC

Para manter o foco na validação das funcionalidades principais, os seguintes itens não serão contemplados nesta fase:

- Criação automática de planos por IA;  
- Vídeos de execução de exercícios;  
- Upload de fotos antes/depois;  
- Streaks avançados de treino;  
- JWT / OAuth;  
- App mobile;  
- Notificações push;  
- Uso de sensores/wearables;  
- Dashboard administrativo;  
- Testes automatizados.

---

## 7. Critérios de Sucesso

A PoC será considerada bem-sucedida caso atenda aos seguintes critérios:

- Permitir cadastro/login com hash de senha;  
- Permitir selecionar e visualizar planos pré-definidos;  
- Registrar e listar treinos com sucesso;  
- Registrar e exibir progresso via gráficos;  
- Atribuir medalhas e pontuação básica;  
- Mostrar integração funcional entre frontend e backend.

---

## 8. Resultados Esperados

Espera-se que, ao final da PoC, o sistema Evolua comprove a viabilidade técnica da solução, mostrando que é possível:

- Gerenciar informações de usuários e treinos em uma plataforma web funcional;  
- Oferecer uma experiência simples e motivadora;  
- Servir como base sólida para futuras expansões, incluindo módulos de IA e automação.

---

## 9. Conclusão

A Prova de Conceito do Evolua tem como principal finalidade validar o núcleo funcional do sistema, demonstrando sua capacidade de apoiar o usuário em sua jornada de evolução física de forma prática e gamificada.

O sucesso desta PoC representará um passo fundamental para o desenvolvimento da versão completa do produto, que poderá incorporar recursos mais avançados como personalização por IA, integração com aplicativos de saúde e análise de dados em tempo real.
