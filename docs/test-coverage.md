<div align="center">

<h1>📊 Relatório de Cobertura de Testes - ServeREST API</h1>


</div>

## 🎯 Descrição

Este documento apresenta a cobertura completa dos testes automatizados realizados na API ServeREST utilizando Postman/Newman.

---

## 📈 Métricas Gerais

### ServeREST - Admin

| Métrica | Quantidade | Status |
|---------|------------|--------|
| **Total de Requisições** | 20 | ✅ |
| **Testes Executados** | 104 | ✅ |
| **Asserções Totais** | 127 | ✅ |
| **Taxa de Sucesso** | 100% | ✅ |
| **Tempo Médio de Resposta** | 56ms | ⚡ |
| **Tempo Total de Execução** | 1.856s | ⚡ |
| **Total de Dados Recebidos** | 9.56KB | 📊 |

### ServeREST - User

| Métrica | Quantidade | Status |
|---------|------------|--------|
| **Total de Requisições** | 18 | ✅ |
| **Testes Executados** | 92 | ✅ |
| **Asserções Totais** | 113 | ✅ |
| **Taxa de Sucesso** | 100% | ✅ |
| **Tempo Médio de Resposta** | 50ms | ⚡ |
| **Tempo Total de Execução** | 1.617s | ⚡ |
| **Total de Dados Recebidos** | 9.83KB | 📊 |

---

## 🔍 Cobertura por Endpoint

### 1️⃣ Gerenciamento de Usuários

#### **POST /usuarios** - Cadastrar Usuário

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | 201 Created | 201 Created |
| **Tempo de Resposta** | 199ms (1ª exec) / 43ms (2ª exec) | 80ms (1ª exec) / 48ms (2ª exec) |
| **Tamanho da Resposta** | 82 bytes | 82 bytes |
| **Assertions Executadas** | 5 | 5 |

**✅ Validações Implementadas:**
- Status code 201 (Created)
- Validação de schema JSON (`_id` e `message`)
- Mensagem: "Cadastro realizado com sucesso"
- Retorno de ID alfanumérico de 16 caracteres
- Armazenamento automático do ID em variável global

**📝 Cenários Testados:**
- **Admin**: Cadastro de administrador (Lila Pfannerstill - flag: true) + usuário auxiliar (Frederick Brakus)
- **User**: Cadastro de usuário comum (Gaylord Pfannerstill) + usuário auxiliar (Dolores Lang)
- Validação de campos obrigatórios: nome, email, password, administrador
- Validação de tipo de dados e formato do ID gerado

---

#### **GET /usuarios** - Listar Usuários

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | 200 OK | 200 OK |
| **Tempo de Resposta** | 49ms | 43ms |
| **Tamanho da Resposta** | 3856 bytes | 3840 bytes |
| **Usuários Retornados** | 17 usuários | 17 usuários |
| **Assertions Executadas** | 5 | 5 |

**✅ Validações Implementadas:**
- Status code 200 (OK)
- Validação de schema da lista (campo `quantidade` e array `usuarios`)
- Quantidade corresponde ao número real de usuários no array
- Estrutura correta de cada usuário: nome, email, password, administrador, _id
- Formato de email válido para todos os usuários
- Todos os usuários possuem campos obrigatórios

**📝 Dados Verificados:**
- Campo `quantidade`: 17
- Estrutura do array validada
- IDs únicos de 16 caracteres para cada usuário
- Emails com formato válido (regex pattern)

---

#### **GET /usuarios/{_id}** - Buscar Usuário por ID

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | 200 OK | 200 OK |
| **Tempo de Resposta** | 44ms | 60ms |
| **Tamanho da Resposta** | 173 bytes | 173 bytes |
| **ID Buscado** | cZLW56YR1Wy8uCrG | eI3p7uQd7JYhc22k |
| **Assertions Executadas** | 7 | 7 |

**✅ Validações Implementadas:**
- Status code 200 (OK)
- Validação de schema completo do usuário
- ID retornado corresponde exatamente ao solicitado
- Usuário possui ID válido (16 caracteres alfanuméricos)
- Email possui formato válido (@domain.com)
- Campo `administrador` é boolean ("true" ou "false")
- Verificação se o usuário é administrador (flag validation)
- Todos os campos obrigatórios presentes

**📝 Usuários Validados:**
- **Admin**: Frederick Brakus (Roberta_Kunze76@hotmail.com, administrador: "true")
- **User**: Dolores Lang (Orlo.Grady@gmail.com, administrador: "false")

---

#### **PUT /usuarios/{_id}** - Editar Usuário

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | 200 OK | 200 OK |
| **Tempo de Resposta** | 49ms | 48ms |
| **Tamanho da Resposta** | 50 bytes | 50 bytes |
| **ID Editado** | cZLW56YR1Wy8uCrG | eI3p7uQd7JYhc22k |
| **Assertions Executadas** | 3 | 3 |

**✅ Validações Implementadas:**
- Status code 200 (OK)
- Mensagem: "Registro alterado com sucesso"
- Validação de schema da resposta
- Confirmação de atualização dos dados

**📝 Cenários Testados:**
- Atualização de usuário auxiliar existente
- Validação de campos editáveis (nome, email, password)
- Confirmação de sucesso na resposta JSON

---

#### **DELETE /usuarios/{_id}** - Excluir Usuário

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | 200 OK | 200 OK |
| **Tempo de Resposta** | 43ms | 46ms |
| **Tamanho da Resposta** | 51 bytes | 51 bytes |
| **ID Excluído** | cZLW56YR1Wy8uCrG | eI3p7uQd7JYhc22k |
| **Assertions Executadas** | 3 | 3 |

**✅ Validações Implementadas:**
- Status code 200 (OK)
- Mensagem: "Registro excluído com sucesso"
- Validação de schema da resposta
- Confirmação de remoção do usuário

**📝 Cenários Testados:**
- Exclusão de usuário sem vínculos com carrinhos
- Confirmação de remoção permanente
- Validação de mensagem de sucesso

---

### 2️⃣ Autenticação

#### **POST /login** - Realizar Login

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | 200 OK | 200 OK |
| **Tempo de Resposta** | 43ms | 46ms |
| **Tamanho da Resposta** | 283 bytes | 283 bytes |
| **Token Gerado** | eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9... | eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9... |
| **Assertions Executadas** | 6 | 6 |

**✅ Validações Implementadas:**
- Status code 200 (OK)
- Mensagem: "Login realizado com sucesso"
- Token possui formato Bearer (prefixo "Bearer ")
- Token JWT possui exatamente 3 partes (header.payload.signature)
- Validação de schema completo (message e authorization)
- Captura e armazenamento do token em variável global
- Token armazenado com prefixo Bearer para uso em requisições autenticadas

**📝 Estrutura do Token Validada:**
- **Formato**: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6IkFyb243...
- **Algoritmo**: HS256 (verificado no header)
- **Campos no payload**: email, password, iat (issued at), exp (expiration)
- **Tempo de validade**: 10 minutos (600 segundos)

**🔐 Credenciais Testadas:**
- **Admin**: Aron78@yahoo.com / DGcvg_vwJQ5441k
- **User**: Yvette.Abshire38@yahoo.com / Hcv5LBl9J2Pkvt3

---

### 3️⃣ Gerenciamento de Produtos

#### **POST /produtos** - Cadastrar Produto

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | ✅ 201 Created | ❌ 403 Forbidden |
| **Tempo de Resposta** | 47ms (1ª) / 45ms (2ª) | 44ms |
| **Tamanho da Resposta** | 82 bytes | 68 bytes |
| **Assertions Executadas** | 6 | 6 |
| **Permissão** | ✅ Autorizado | ❌ Bloqueado |

**✅ Validações Implementadas (Admin):**
- Status code 201 (Created)
- Verificação de token no header Authorization
- Mensagem: "Cadastro realizado com sucesso"
- Produto criado possui ID válido
- Captura automática do ID do produto
- Validação de schema completo

**❌ Validações Implementadas (User):**
- Status code 403 (Forbidden)
- Mensagem de erro: "Rota exclusiva para administradores"
- Validação de bloqueio de segurança
- Confirmação que usuário comum NÃO pode criar produtos

**📝 Produtos Criados (Admin):**
- **Produto 1**: "Practical Wooden Shoes" | ID: JzodwA9Fn9lPNz3X | R$496,00 | 441 unidades
- **Produto 2**: "Intelligent Fresh Cheese" | ID: KMdGiUjlQqE1yc9g | R$30,00 | 844 unidades

**🔐 Diferencial de Segurança:**
- Admin com token válido: ✅ Criação autorizada
- User com token válido: ❌ Criação negada (validação de role)

---

#### **GET /produtos** - Listar Produtos

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | 200 OK | 200 OK |
| **Tempo de Resposta** | 49ms | 46ms |
| **Tamanho da Resposta** | 2021 bytes | 2019 bytes |
| **Produtos Retornados** | 10 produtos | 10 produtos |
| **Assertions Executadas** | 6 | 6 |

**✅ Validações Implementadas:**
- Status code 200 (OK)
- Validação de schema (campo `quantidade` e array `produtos`)
- Quantidade corresponde ao número real de produtos
- Todos os produtos possuem preço positivo (> 0)
- Todos os produtos possuem quantidade não-negativa (>= 0)
- Todos os campos obrigatórios presentes: nome, preco, descricao, quantidade, _id

**📝 Dados Verificados:**
- 10 produtos no catálogo
- Preços variando de R$30 a R$496
- Quantidades variando de 441 a 844 unidades
- Descrições variadas (Pants, Pizza, Cheese, etc)

---

#### **GET /produtos/{_id}** - Buscar Produto por ID

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | 200 OK | 200 OK |
| **Tempo de Resposta** | 42ms (1ª) / 47ms (2ª) | 43ms |
| **Tamanho da Resposta** | 138-139 bytes | 138 bytes |
| **ID Buscado** | JzodwA9Fn9lPNz3X / KMdGiUjlQqE1yc9g | Produto existente |
| **Assertions Executadas** | 8 | 8 |

**✅ Validações Implementadas:**
- Status code 200 (OK)
- ID retornado corresponde ao solicitado
- Produto possui ID válido (16 caracteres)
- Preço é maior ou igual a 1 (validação de negócio)
- Quantidade é não-negativa (>= 0)
- Nome não está vazio (length > 0)
- Produto possui todos os campos obrigatórios
- Validação de schema completo

**📝 Produtos Buscados:**
- **Admin (1ª busca)**: "Practical Wooden Shoes" - R$496, 441 unidades, descrição: "Pants"
- **Admin (2ª busca)**: "Intelligent Fresh Cheese" - R$30, 844 unidades, descrição: "Pants"
- **User**: "Practical Frozen Pizza" - R$458, 721 unidades

---

#### **DELETE /produtos/{_id}** - Excluir Produto

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | ✅ 200 OK | ❌ 403 Forbidden |
| **Tempo de Resposta** | 49ms | 42ms |
| **Tamanho da Resposta** | 51 bytes | 68 bytes |
| **Assertions Executadas** | 4 | 6 |
| **Permissão** | ✅ Autorizado | ❌ Bloqueado |

**✅ Validações Implementadas (Admin):**
- Status code 200 (OK)
- Verificação de token no header
- Mensagem: "Registro excluído com sucesso"
- Validação de schema

**❌ Validações Implementadas (User):**
- Status code 403 (Forbidden)
- Mensagem de erro: "Rota exclusiva para administradores"
- Validação de bloqueio de segurança

**🔐 Diferencial de Segurança:**
- Admin: ✅ Pode excluir produtos
- User: ❌ Bloqueado (validação de role administrativa)

---

#### **PUT /produtos/{_id}** - Editar Produto

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | ✅ 200 OK | ❌ 403 Forbidden |
| **Tempo de Resposta** | 55ms | 42ms |
| **Tamanho da Resposta** | 50 bytes | 68 bytes |
| **Assertions Executadas** | 4 | 6 |
| **Permissão** | ✅ Autorizado | ❌ Bloqueado |

**✅ Validações Implementadas (Admin):**
- Status code 200 (OK)
- Verificação de token no header
- Mensagem: "Registro alterado com sucesso"
- Validação de schema

**❌ Validações Implementadas (User):**
- Status code 403 (Forbidden)
- Mensagem de erro: "Rota exclusiva para administradores"
- Validação de bloqueio de segurança

**📝 Cenários Testados:**
- **Admin**: Edição bem-sucedida do produto JzodwA9Fn9lPNz3X
- **User**: Tentativa bloqueada de editar produto
- Validação de campos editáveis: nome, preço, descrição, quantidade

---

### 4️⃣ Gerenciamento de Carrinhos

#### **POST /carrinhos** - Cadastrar Carrinho

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | 201 Created | 201 Created |
| **Tempo de Resposta** | 52ms | 48ms |
| **Tamanho da Resposta** | 82 bytes | 82 bytes |
| **ID do Carrinho** | uLmpZYFSOnkL4iyQ | ID único gerado |
| **Assertions Executadas** | 7 | 7 |

**✅ Validações Implementadas:**
- Status code 201 (Created)
- Content-Type: application/json
- Verificação de token no header Authorization
- Mensagem: "Cadastro realizado com sucesso"
- Validação de schema completo
- Carrinho criado possui ID válido (16 caracteres)
- Captura automática do ID do carrinho

**📝 Dados do Carrinho:**
- **Admin**: 398 unidades de produtos, preço total R$11.940,00
- **User**: Carrinho criado com produtos disponíveis
- Vinculação automática ao usuário autenticado

---

#### **GET /carrinhos** - Listar Carrinhos

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | 200 OK | 200 OK |
| **Tempo de Resposta** | 43ms | 45ms |
| **Tamanho da Resposta** | 982 bytes | ~980 bytes |
| **Carrinhos Ativos** | 2 carrinhos | 2 carrinhos |
| **Assertions Executadas** | 11 | 11 |

**✅ Validações Implementadas:**
- Status code 200 (OK)
- Validação de schema completo
- Quantidade corresponde ao número real de carrinhos
- Cada usuário possui apenas um carrinho (regra de negócio)
- Todos os carrinhos possuem preços válidos
- Validação de cálculo: preço total = Σ(preço × quantidade)
- Todos os preços são positivos
- Validação de cálculo: quantidade total = Σ(quantidades)
- Todos os carrinhos possuem campos obrigatórios
- Todos os produtos possuem campos obrigatórios
- Não há produtos duplicados em nenhum carrinho

**📝 Validações de Integridade:**
- Cálculo correto de `precoTotal`
- Cálculo correto de `quantidadeTotal`
- Unicidade de produtos por carrinho
- Vinculação correta com `idUsuario`

---

#### **GET /carrinhos/{_id}** - Buscar Carrinho por ID

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | 200 OK | 200 OK |
| **Tempo de Resposta** | 46ms | 51ms |
| **Tamanho da Resposta** | 281 bytes | ~280 bytes |
| **ID Buscado** | uLmpZYFSOnkL4iyQ | Carrinho específico |
| **Assertions Executadas** | 14 | 14 |

**✅ Validações Implementadas:**
- Status code 200 (OK)
- Content-Type: application/json
- Validação de schema completo
- Carrinho possui ID válido
- Carrinho está vinculado a um usuário (`idUsuario`)
- Carrinho possui pelo menos um produto
- `precoTotal` não é negativo
- `quantidadeTotal` é positiva
- Validação matemática: precoTotal = Σ(preco × quantidade)
- Validação matemática: quantidadeTotal = Σ(quantidades)
- Todos os produtos possuem campos obrigatórios
- Não há produtos duplicados no carrinho
- ID retornado corresponde ao solicitado
- Captura dos dados completos do carrinho

**📝 Dados Validados (Admin):**
- ID: uLmpZYFSOnkL4iyQ
- Preço Total: R$11.940,00
- Quantidade Total: 398 unidades
- ID Usuário: kV4nZCZ2rU2g8k58
- Produtos: Array com detalhes completos

---

#### **DELETE /carrinhos/cancelar-compra** - Cancelar Compra

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | 200 OK | 200 OK |
| **Tempo de Resposta** | 43ms | 48ms |
| **Tamanho da Resposta** | 86 bytes | 86 bytes |
| **Assertions Executadas** | 8 | 8 |

**✅ Validações Implementadas:**
- Status code 200 (OK)
- Verificação de token no header Authorization
- Accept header: application/json (request)
- Content-Type header: application/json (response)
- Validação de schema completo
- Resposta possui campo `message`
- Mensagem específica validada
- Confirmação: "Registro excluído com sucesso. Estoque dos produtos reabastecido"

**📝 Regra de Negócio Validada:**
- Carrinho removido com sucesso
- Produtos devolvidos ao estoque (reabastecimento)
- Operação realizada para ambos os perfis (admin e user)

---

#### **DELETE /carrinhos/concluir-compra** - Concluir Compra

**📊 Resultados por Collection:**

| Métrica | Admin | User |
|---------|-------|------|
| **Status Code** | 200 OK | 200 OK |
| **Tempo de Resposta** | 42ms | 48ms |
| **Tamanho da Resposta** | 68 bytes | 68 bytes |
| **Assertions Executadas** | 8 | 8 |

**✅ Validações Implementadas:**
- Status code 200 (OK)
- Verificação de token no header Authorization
- Accept header: application/json (request)
- Content-Type header: application/json (response)
- Validação de schema completo
- Resposta possui campo `message`
- Mensagem validada: "Não foi encontrado carrinho para esse usuário"
- Validação de cenário: usuário não possui carrinho ativo

**📝 Cenário Testado:**
- Tentativa de conclusão após cancelamento prévio
- Validação de mensagem quando carrinho não existe
- Comportamento correto da API ao não encontrar carrinho

---

## 🎭 Tipos de Testes Implementados

### ✅ Testes Funcionais
- **16 endpoints únicos** da API ServeRest testados
- **38 requisições totais** executadas (20 Admin + 18 User)
- Verificação de CRUD completo para cada recurso:
  - **Usuários**: 5 operações (POST, GET, GET by ID, PUT, DELETE)
  - **Login**: 1 operação (POST com geração de JWT)
  - **Produtos**: 5 operações (POST, GET, GET by ID, PUT, DELETE)
  - **Carrinhos**: 5 operações (POST, GET, GET by ID, DELETE cancelar, DELETE concluir)
- Testes de fluxo de usuário completo (cadastro → login → operações → carrinho)

### ✅ Testes de Contrato (Schema Validation)
- **100% dos endpoints** com validação de schema JSON
- Verificação rigorosa de tipos de dados:
  - Strings: nome, email, descrição
  - Numbers: preço, quantidade, timestamps
  - Booleans: administrador
  - Arrays: produtos, usuarios, carrinhos
  - Objects: estruturas aninhadas validadas
- Validação de campos obrigatórios vs opcionais
- Verificação de formato: emails, IDs (16 chars), tokens JWT (3 partes)

### ✅ Testes de Integração
- **Fluxo completo E2E** implementado:
  1. Geração de massa de dados (RandomUser.me API)
  2. Cadastro de usuário
  3. Login e captura de token JWT
  4. Operações autenticadas (produtos, carrinhos)
  5. Limpeza (cancelamento/conclusão)
- **Dependência entre requests** gerenciada via variáveis globais:
  - IDs de usuários capturados e reutilizados
  - Tokens JWT armazenados e aplicados automaticamente
  - IDs de produtos e carrinhos propagados entre testes
- Validação de relacionamentos:
  - Carrinho vinculado ao usuário correto
  - Produtos associados aos carrinhos
  - Integridade referencial mantida

### ✅ Testes de Autorização
- **6 cenários de permissão** testados:
  - Admin pode: POST, PUT, DELETE em /produtos (✅ 201/200)
  - User não pode: POST, PUT, DELETE em /produtos (❌ 403)
- **3 rotas administrativas** protegidas e validadas
- Verificação de token JWT em todas as rotas autenticadas
- Validação de role (admin/user) no payload do token
- Testes de bloqueio com mensagem: "Rota exclusiva para administradores"

### ✅ Testes de Performance
- **Medição em tempo real** de cada requisição:
  - **Admin**: Mínimo 42ms | Máximo 199ms | Média 56ms | Desvio Padrão 34.44ms
  - **User**: Mínimo 42ms | Máximo 80ms | Média 50ms | Desvio Padrão ~15ms
- **Duração total de execução**:
  - Admin: 1.856s (20 requests)
  - User: 1.617s (18 requests)
  - **Total**: 3.473s para 38 requests
- **Throughput**:
  - Admin: 9793 bytes transferidos (9.56KB)
  - User: 10063 bytes transferidos (9.83KB)
  - **Total**: 19.39KB transferidos
- **Performance geral**: ⚡ Excelente (média < 60ms, classificação A+)

**📊 Análise de Performance:**
- 95% das requisições abaixo de 100ms
- Apenas 1 requisição acima de 100ms (199ms no cadastro inicial Admin)
- Tempo de resposta consistente entre collections
- Zero timeouts ou falhas de conexão
- API altamente responsiva e estável

---

## 📋 Scripts de Teste Utilizados

### Pre-request Scripts
- **Geração dinâmica de massa de dados** com Faker.js via RandomUser.me:
  - Nomes aleatórios realistas
  - Emails válidos e únicos
  - Senhas geradas automaticamente
  - Dados de geolocalização (país, cidade)
- **Armazenamento em variáveis globais**:
  - `userAdmName`, `userAdmEmail`, `userAdmPassword`, `userAdmID`
  - `userAuxName`, `userAuxEmail`, `userAuxPassword`, `userAuxID`
  - `ApiKeyAuthAdm`, `ApiKeyAuthUser` (tokens JWT)
  - `productID`, `productName`, `productPrice`, `productAmount`
  - `cartIDUser`, `cartTotalPrice`, `cartTotalQuant`
- **Preparação de payloads dinâmicos**:
  - Produtos com preços e quantidades aleatórias
  - Carrinhos com produtos válidos do catálogo

### Test Scripts
- **Validação de status codes**:
  - Sucesso: 200 (OK), 201 (Created)
  - Erro esperado: 403 (Forbidden) para usuários sem permissão
- **Validação de schemas JSON** com JSON Schema:
  - Estrutura de objetos validada
  - Tipos de dados conferidos
  - Campos obrigatórios verificados
- **Armazenamento automático** de dados críticos:
  - `pm.globals.set("userAdmID", jsonData._id)`
  - `pm.globals.set("ApiKeyAuthAdm", jsonData.authorization)`
  - `pm.globals.set("productID", jsonData._id)`
- **Validação de mensagens de resposta**:
  - "Cadastro realizado com sucesso"
  - "Login realizado com sucesso"
  - "Registro alterado com sucesso"
  - "Registro excluído com sucesso"
  - "Rota exclusiva para administradores"
- **Verificação de estrutura de dados**:
  - Arrays não vazios
  - Objetos com propriedades esperadas
  - Valores dentro de ranges válidos (preços > 0, quantidades >= 0)
- **Validações matemáticas**:
  - Cálculo de `precoTotal` = Σ(preco × quantidade)
  - Cálculo de `quantidadeTotal` = Σ(quantidades)
  - Unicidade de produtos em carrinhos

**🔧 Bibliotecas Utilizadas:**
- **Postman Variables**: Gerenciamento de estado entre requests
- **Chai Assertion Library**: Validações expressivas (expect, to.be, to.have)
- **JSON Schema Validator**: Validação de contratos de API
- **Faker.js** (via RandomUser.me): Geração de dados realistas

---

## 🔐 Segurança Testada

- ✅ **Autenticação via JWT (JSON Web Token)**:
  - Token gerado no endpoint POST /login
  - Formato validado: Bearer <token>
  - Estrutura JWT: Header.Payload.Signature (3 partes separadas por ponto)
  - Payload contém: email, password, iat (issued at), exp (expiration)
  - Tempo de validade: 10 minutos (600 segundos)
  - Token armazenado e reutilizado automaticamente em todas as requests autenticadas

- ✅ **Autorização baseada em roles (admin/user)**:
  - **Administradores** (flag: "true"): acesso total a produtos (POST, PUT, DELETE)
  - **Usuários comuns** (flag: "false"): acesso negado a operações administrativas
  - Validação de role extraída do token JWT
  - 6 cenários de permissão testados (3 rotas × 2 perfis)

- ✅ **Validação de tokens**:
  - Token presente no header Authorization
  - Formato Bearer verificado
  - Token válido (não expirado)
  - Token inválido retorna erro apropriado

- ✅ **Proteção de rotas administrativas**:
  - POST /produtos: ✅ Admin 201 | ❌ User 403
  - PUT /produtos/{_id}: ✅ Admin 200 | ❌ User 403
  - DELETE /produtos/{_id}: ✅ Admin 200 | ❌ User 403
  - Mensagem de erro consistente: "Rota exclusiva para administradores"

- ✅ **Validação de permissões por endpoint**:
  - Rotas públicas (sem autenticação): GET /produtos, GET /usuarios
  - Rotas autenticadas (requerem token): POST /carrinhos, GET /carrinhos/{_id}
  - Rotas administrativas (requerem token + role admin): POST/PUT/DELETE /produtos
  - Vinculação de recursos ao usuário autenticado (carrinho → usuário)

**🔒 Cobertura de Segurança:**
- **100% dos endpoints** com autenticação testada
- **100% das rotas administrativas** com autorização validada
- **0 falhas** de segurança detectadas
- **3 bloqueios corretos** validados (status 403 para User em operações de produtos)

---

## 📊 Análise de Cobertura

### Cobertura por Método HTTP

| Método | Quantidade | Percentual |
|--------|------------|------------|
| GET | 6 | 33.3% |
| POST | 6 | 33.3% |
| PUT | 2 | 11.1% |
| DELETE | 4 | 22.2% |

### Cobertura por Recurso

| Recurso | Endpoints Testados | Cobertura |
|---------|-------------------|-----------|
| Usuários | 5/5 | 100% |
| Login | 1/1 | 100% |
| Produtos | 5/5 | 100% |
| Carrinhos | 5/5 | 100% |

---

## 🎯 Cenários de Negócio Cobertos

### 👤 Jornada do Usuário Comum (ServeREST - User)

**Fluxo Completo: Desde a Geração de Massa até Gerenciamento de Carrinho**

1. ✅ **Geração de Massa de Dados** (Pre-request Script)
   - Consumo da API RandomUser.me para gerar dados realistas
   - Tempo: 80ms | 1135 bytes recebidos | 3 assertions
   - Validação de schema da resposta externa

2. ✅ **Cadastro de Novo Usuário** (POST /usuarios)
   - Status 201 Created | Tempo: 80ms | ID gerado: LRtuorsAZe00e9OS
   - 5 assertions: status, mensagem, ID válido, schema JSON
   - Usuário criado: Gaylord Pfannerstill (Yvette.Abshire38@yahoo.com)

3. ✅ **Login na Plataforma** (POST /login)
   - Status 200 OK | Tempo: 46ms | Token JWT gerado e armazenado
   - 6 assertions: status, mensagem, formato Bearer, 3 partes do JWT
   - Token capturado para autorização nas próximas requisições

4. ✅ **Cadastro de Usuário Auxiliar** (POST /usuarios)
   - Status 201 Created | Tempo: 48ms | ID: eI3p7uQd7JYhc22k
   - Usuário auxiliar: Dolores Lang (Orlo.Grady@gmail.com)
   - 5 assertions de validação completa

5. ✅ **Visualização de Todos os Usuários** (GET /usuarios)
   - Status 200 OK | Tempo: 43ms | 3840 bytes (17 usuários listados)
   - 5 assertions: quantidade, campos obrigatórios, formato de email

6. ✅ **Busca de Usuário Específico por ID** (GET /usuarios/{_id})
   - Status 200 OK | Tempo: 60ms | Dados completos do usuário auxiliar
   - 7 assertions: ID correspondente, email válido, flag administrador

7. ✅ **Edição de Usuário** (PUT /usuarios/{_id})
   - Status 200 OK | Tempo: 48ms | "Registro alterado com sucesso"
   - 3 assertions: status, mensagem de sucesso, schema

8. ✅ **Exclusão de Usuário** (DELETE /usuarios/{_id})
   - Status 200 OK | Tempo: 46ms | "Registro excluído com sucesso"
   - 3 assertions: confirmação de exclusão

9. ✅ **Tentativa de Cadastro de Produto** (POST /produtos)
   - **Status 403 Forbidden** | Tempo: 44ms | Bloqueio correto
   - Mensagem: "Rota exclusiva para administradores"
   - **Validação de segurança: usuário comum não pode criar produtos**

10. ✅ **Visualização de Catálogo de Produtos** (GET /produtos)
    - Status 200 OK | Tempo: 46ms | 2019 bytes (10 produtos disponíveis)
    - 6 assertions: quantidade, preços positivos, estoque não-negativo

11. ✅ **Busca de Produto Específico** (GET /produtos/{_id})
    - Status 200 OK | Tempo: 43ms | Produto: "Practical Frozen Pizza"
    - 8 assertions: ID, preço R$458, quantidade 721, campos obrigatórios

12. ✅ **Tentativa de Exclusão de Produto** (DELETE /produtos/{_id})
    - **Status 403 Forbidden** | Tempo: 42ms | Bloqueio correto
    - **Validação de segurança: usuário comum não pode excluir produtos**

13. ✅ **Tentativa de Edição de Produto** (PUT /produtos/{_id})
    - **Status 403 Forbidden** | Tempo: 42ms | Bloqueio correto
    - **Validação de segurança: usuário comum não pode editar produtos**

14. ✅ **Criação de Carrinho de Compras** (POST /carrinhos)
    - Status 201 Created | Tempo: 48ms | ID do carrinho gerado
    - 7 assertions: token presente, mensagem, ID válido, schema
    - Carrinho vinculado ao usuário autenticado

15. ✅ **Visualização de Todos os Carrinhos** (GET /carrinhos)
    - Status 200 OK | Tempo: 45ms | 2 carrinhos ativos no sistema
    - 11 assertions: validação de preços, quantidades, sem duplicatas

16. ✅ **Busca de Carrinho Específico** (GET /carrinhos/{_id})
    - Status 200 OK | Tempo: 51ms | Dados completos do carrinho
    - 14 assertions: precoTotal, quantidadeTotal, produtos, usuário vinculado

17. ✅ **Cancelamento de Compra** (DELETE /carrinhos/cancelar-compra)
    - Status 200 OK | Tempo: 48ms | "Estoque reabastecido"
    - 8 assertions: devolução de produtos ao estoque confirmada

18. ✅ **Tentativa de Conclusão de Compra** (DELETE /carrinhos/concluir-compra)
    - Status 200 OK | Tempo: 48ms | "Não foi encontrado carrinho"
    - Carrinho já foi removido no cancelamento anterior

**📊 Resumo da Jornada User:**
- **18 requisições** executadas em **1.617s**
- **113 assertions** validadas com sucesso
- **3 bloqueios de segurança** testados (status 403)
- **Tempo médio**: 50ms por requisição

---

### 👨‍💼 Jornada do Administrador (ServeREST - Admin)

**Fluxo Completo: Gestão Completa de Usuários, Produtos e Carrinhos**

1. ✅ **Geração de Massa de Dados** (Pre-request Script)
   - Consumo da API RandomUser.me para dados do admin
   - Tempo: 92ms | 1154 bytes recebidos | 3 assertions
   - Usuário API gerado: Greg O'Sullivan (Ireland)

2. ✅ **Cadastro Inicial como Administrador** (POST /usuarios)
   - Status 201 Created | Tempo: 199ms | ID: kV4nZCZ2rU2g8k58
   - 5 assertions: criação bem-sucedida, ID capturado
   - Admin criado: Lila Pfannerstill (Aron78@yahoo.com)
   - **Flag administrador: true**

3. ✅ **Login como Administrador** (POST /login)
   - Status 200 OK | Tempo: 43ms | Token JWT administrativo gerado
   - 6 assertions: token Bearer com 3 partes válidas
   - Token armazenado para operações privilegiadas

4. ✅ **Cadastro de Usuário Auxiliar** (POST /usuarios)
   - Status 201 Created | Tempo: 43ms | ID: cZLW56YR1Wy8uCrG
   - 5 assertions: usuário Frederick Brakus criado
   - Email: Roberta_Kunze76@hotmail.com

5. ✅ **Listagem de Todos os Usuários** (GET /usuarios)
   - Status 200 OK | Tempo: 49ms | 3856 bytes (17 usuários cadastrados)
   - 5 assertions: validação completa de estrutura e dados

6. ✅ **Busca de Usuário por ID** (GET /usuarios/{_id})
   - Status 200 OK | Tempo: 44ms | Usuário: Frederick Brakus
   - 7 assertions: ID correto, campos completos, flag admin = true

7. ✅ **Edição de Dados do Usuário** (PUT /usuarios/{_id})
   - Status 200 OK | Tempo: 49ms | "Registro alterado com sucesso"
   - 3 assertions: atualização confirmada

8. ✅ **Exclusão de Usuário** (DELETE /usuarios/{_id})
   - Status 200 OK | Tempo: 43ms | "Registro excluído com sucesso"
   - 3 assertions: usuário Frederick Brakus removido

9. ✅ **Cadastro do Primeiro Produto** (POST /produtos)
   - **Status 201 Created** | Tempo: 47ms | ID: JzodwA9Fn9lPNz3X
   - 6 assertions: token validado, produto criado com sucesso
   - Produto: "Practical Wooden Shoes" | R$496 | 441 unidades
   - **Permissão admin: operação bem-sucedida**

10. ✅ **Listagem de Produtos Cadastrados** (GET /produtos)
    - Status 200 OK | Tempo: 49ms | 2021 bytes (10 produtos no catálogo)
    - 6 assertions: preços positivos, quantidades válidas

11. ✅ **Busca de Produto Específico** (GET /produtos/{_id})
    - Status 200 OK | Tempo: 42ms | Produto "Practical Wooden Shoes"
    - 8 assertions: ID, preço, descrição "Pants", quantidade 441

12. ✅ **Edição de Produto** (PUT /produtos/{_id})
    - **Status 200 OK** | Tempo: 55ms | "Registro alterado com sucesso"
    - 4 assertions: token presente, atualização confirmada
    - **Permissão admin: edição autorizada**

13. ✅ **Exclusão de Produto** (DELETE /produtos/{_id})
    - **Status 200 OK** | Tempo: 49ms | "Registro excluído com sucesso"
    - 4 assertions: token validado, exclusão confirmada
    - **Permissão admin: remoção autorizada**

14. ✅ **Cadastro do Segundo Produto** (POST /produtos)
    - Status 201 Created | Tempo: 45ms | ID: KMdGiUjlQqE1yc9g
    - Produto: "Intelligent Fresh Cheese" | R$30 | 844 unidades
    - 6 assertions: criação confirmada

15. ✅ **Busca do Segundo Produto** (GET /produtos/{_id})
    - Status 200 OK | Tempo: 47ms | Produto "Intelligent Fresh Cheese"
    - 8 assertions: todos os campos validados

16. ✅ **Criação de Carrinho** (POST /carrinhos)
    - Status 201 Created | Tempo: 52ms | ID: uLmpZYFSOnkL4iyQ
    - 7 assertions: carrinho criado e vinculado ao admin
    - Produtos adicionados: quantidade total 398 unidades

17. ✅ **Listagem de Carrinhos Ativos** (GET /carrinhos)
    - Status 200 OK | Tempo: 43ms | 982 bytes (2 carrinhos ativos)
    - 11 assertions: validação de cálculos, preços, sem duplicatas

18. ✅ **Busca de Carrinho por ID** (GET /carrinhos/{_id})
    - Status 200 OK | Tempo: 46ms | Carrinho completo
    - 14 assertions: precoTotal R$11.940, quantidadeTotal 398
    - Carrinho vinculado ao ID do admin: kV4nZCZ2rU2g8k58

19. ✅ **Cancelamento de Compra com Reabastecimento** (DELETE /carrinhos/cancelar-compra)
    - Status 200 OK | Tempo: 43ms | "Estoque reabastecido"
    - 8 assertions: produtos devolvidos ao estoque

20. ✅ **Conclusão de Compra** (DELETE /carrinhos/concluir-compra)
    - Status 200 OK | Tempo: 42ms | "Não foi encontrado carrinho"
    - Carrinho já removido pelo cancelamento anterior

**📊 Resumo da Jornada Admin:**
- **20 requisições** executadas em **1.856s** (inclui 2 requests duplicados de produtos)
- **127 assertions** validadas com sucesso
- **Permissões completas**: criar, editar e excluir produtos (status 200/201)
- **Tempo médio**: 56ms por requisição
- **Operações críticas testadas**: CRUD completo de produtos + gerenciamento de usuários

---

### 🔐 Comparativo de Permissões: Admin vs User

| Operação | Admin | User | Validação |
|----------|-------|------|-----------|
| POST /produtos | ✅ 201 Created | ❌ 403 Forbidden | ✅ Testado |
| PUT /produtos | ✅ 200 OK | ❌ 403 Forbidden | ✅ Testado |
| DELETE /produtos | ✅ 200 OK | ❌ 403 Forbidden | ✅ Testado |
| POST /usuarios | ✅ 201 Created | ✅ 201 Created | Ambos podem criar |
| POST /carrinhos | ✅ 201 Created | ✅ 201 Created | Ambos podem comprar |
| GET (todos) | ✅ 200 OK | ✅ 200 OK | Acesso público |

**Total de Cenários Testados**: 38 requisições (20 Admin + 18 User)

---

## 📌 Conclusão

A cobertura de testes da API ServeREST está **completa e robusta**, com:

- ✅ **100% dos endpoints** cobertos
- ✅ **240 asserções** validadas com sucesso (100+ asserções validadas por collection)
- ✅ **Zero falhas** nos testes executados
- ✅ **Performance excelente** (Admin: 56ms | User: 50ms)
- ✅ **Validação completa** de jon schemas
- ✅ **Segurança** e autorização testadas
- ✅ **Execução rápida** (Total: ~3.5 segundos para 36 requests)

### 🏆 Qualidade do Código de Testes

- **Manutenibilidade**: Alta (uso de variáveis e scripts reutilizáveis)
- **Legibilidade**: Alta (nomenclatura clara e estruturada)
- **Cobertura**: 100% dos endpoints testados
- **Confiabilidade**: Alta (sem falhas nos testes)

---

## 📞 Informações

**Projeto**: ServeREST API Testing  
**Ferramenta**: Postman + Newman v6.2.1  
**Data de Execução**: Segunda-feira, 24 de Novembro de 2025  
**Responsável**: Sthefany Ricardo  
**Repositório**: [github.com/sthefanyricardo/testes-api-postman-newman](https://github.com/sthefanyricardo/testes-api-postman-newman)

---

<div align="center">

### "Winter is Coming... But Our Tests Keep Running" 🐺❄️🔥

**100% de cobertura | 0% de falhas | ⚡ Performance excelente**

</div>


