# Dieta-Academia
API da aplicação de controle de gastos pessoais.

## Endpoints

- Refeição
    - [Cadastrar refeição](#cadastrar-refeição)
    - Apagar refeição
    - Alterar refeição
    - Listar todas as refeições
    - [Detalhar uma refeição](#detalhar-refeição)
- Treino
    - [Cadastrar treino](#cadastrar-treino)
    - Apagar treino
    - Alterar treino
    - Listar todas os treinos
    - [Detalhar um treino](#detalhar-treino)


---

### Cadastrar Refeição

`POST` /appnutrifit/api/refeição

| campo | tipo | obrigatório | descrição
|-------|------|:-------------:|----
| numero_ref | inteiro | sim | número da refeição cadastrada pelo usuário 
| data | data | não | a data em que o usuário cadastrou a refeição
| categoria_ref | texto | sim | a categoria da refeição previamente cadastrada
| tipo_ref | texto | sim | tipo de refeição a ser feita (líquida ou sólida)
| descricao | texto | não | um texto com detalhes sobre a refeição

  **Exemplo de corpo de requisição**

```js 
{
    numero_ref: 1,
    data: '2023-02-28',
    categoria_ref: 'desjejum',
    tipo_ref: 'líquida',
    descricao: 'desjejum que deve ser feito até às 8h'
}
```

**Respostas**

| código | descrição
|-|-
|201| refeição cadastrada com sucesso
|400| a validação dos campos falhou

---

### Detalhar Refeição

`GET` /appnutrifit/api/refeicao/{id}

**Respostas**

| código | descrição
|-|-
|200| os dados da refeição foram retornados no corpo da resposta
|404| não existe refeição com a categoria informada

**Exemplo de corpo da resposta**
```js 
{
    numero_ref: 1,
    data: '2023-02-28',
    categoria: {
        categoria_ref: 'desjejum',
        nome: 'plano A',
    }
    tipo_ref: {
        tipo_ref: 'líquida',
        nome: 'hipercalórico',
    },
    descricao: 'desjejum que deve ser feito até às 8h'
}
```
### Cadastrar Treino

`POST` /appnutrifit/api/treino

| campo | tipo | obrigatório | descrição
|-------|------|:-------------:|----
| data_treino | texto | sim | data do treino cadastrada pelo usuário, em dia da semana
| data | data | sim | a data em que o usuário cadastrou o treino
| categoria_treino | texto | sim | a categoria do treino previamente cadastrado
| descricao | texto | não | um texto com detalhes sobre o treino

  **Exemplo de corpo de requisição**

```js 
{
    data_treino: 'segunda-feira',
    data: '2023-02-28',
    categoria_treino: 'quadríceps',
    descricao: 'exercícios de quadríceps'
}
```

**Respostas**

| código | descrição
|-|-
|201| treino cadastrado com sucesso
|400| a validação dos campos falhou

---

### Detalhar Treino

`GET` /appnutrifit/api/treino/{id}

**Respostas**

| código | descrição
|-|-
|200| os dados do treino foram retornados no corpo da resposta
|404| não existe treino com a categoria informada

**Exemplo de corpo da resposta**
```js 
{
    data_treino: 'segunda-feira',
    data: '2023-02-28',
    categoria: {
        categoria_treino: 'quadríceps',
        nome: 'plano A',
    }
    descricao: 'exercícios de quadríceps'
}