<div align="center">

# 🧪 API Test JSONPlaceholder

![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![JSON](https://img.shields.io/badge/JSON-000000?style=for-the-badge&logo=json&logoColor=white)
![API Testing](https://img.shields.io/badge/API%20Testing-4CAF50?style=for-the-badge&logo=checkmarx&logoColor=white)

*Coleção de testes automatizados para validação de API REST utilizando JSONPlaceholder*

[🚀 Começar](#-como-usar) • [📚 Documentação](#-principais-testes-implementados) • [🔧 Instalação](#-como-usar) • [📄 Licença](#-licença)

</div>

---

## 📋 Visão Geral

Este projeto demonstra domínio em **validação de contratos de API**, **organização de testes automatizados** e **boas práticas** para versionamento e colaboração via GitHub. A coleção de testes foi desenvolvida para a API pública **JSONPlaceholder**, validando todos os principais endpoints com scripts de teste abrangentes.

## 🎯 Objetivos

- Demonstrar proficiência em testes de API usando Postman
- Implementar validação rigorosa de contratos (Schema Validation)
- Organizar testes de forma estruturada e reutilizável
- Aplicar boas práticas de automação de testes
- Documentar adequadamente os testes e processos

## 🌐 API Utilizada

**JSONPlaceholder**: https://jsonplaceholder.typicode.com/

Uma API REST gratuita para testes e prototipagem, que simula recursos como:
- Posts (100 items)
- Comments (500 items)
- Users (10 items)
- Albums (100 items)
- Photos (5000 items)
- Todos (200 items)

## 📁 Estrutura do Projeto

```
api-test-JSONPlaceholder/
├── collections/
│   ├── jsonplaceholder-tests.postman_collection.json
│   └── jsonplaceholder-environment.postman_environment.json
├── schemas/
│   ├── post-schema.json
│   ├── user-schema.json
│   └── comment-schema.json
├── docs/
├── screenshots/
└── README.md
```

## 🚀 Como Usar

### 1. Importar no Postman

1. **Baixe os arquivos**:
   - `jsonplaceholder-tests.postman_collection.json`
   - `jsonplaceholder-environment.postman_environment.json`

2. **Importe no Postman**:
   - Abra o Postman
   - Clique em "Import"
   - Selecione os arquivos baixados
   - Confirme a importação

3. **Configure o ambiente**:
   - Selecione o ambiente "JSONPlaceholder Environment"
   - Verifique se as variáveis estão configuradas corretamente

### 2. Executar os Testes

#### Execução Individual
- Navegue pelas pastas organizadas por recurso
- Execute requests individuais
- Visualize os resultados dos testes na aba "Test Results"

#### Execução em Lote
- Clique no nome da coleção "JSONPlaceholder Tests"
- Clique em "Run Collection"
- Configure as opções de execução (delay, iterações)
- Execute e visualize o relatório completo

## 🧪 Principais Testes Implementados

### 📝 Posts
- **GET All Posts**: Valida estrutura, quantidade e campos obrigatórios
- **GET Single Post**: Verifica dados específicos e integridade
- **POST Create Post**: Testa criação com validação de resposta
- **PUT Update Post**: Valida atualização completa
- **DELETE Post**: Confirma remoção bem-sucedida

### 💬 Comments
- **GET All Comments**: Valida estrutura e formato de email
- **GET Comments by Post**: Testa relacionamento post-comentário

### 👥 Users
- **GET All Users**: Valida estrutura complexa (endereço, empresa)
- **GET Single User**: Verifica dados pessoais completos
- **GET User Posts**: Testa relacionamento usuário-posts

### 🖼️ Albums & Photos
- **GET All Albums**: Valida estrutura básica
- **GET Album Photos**: Testa URLs e relacionamentos

### ✅ Todos
- **GET All Todos**: Valida estrutura e tipos de dados
- **GET User Todos**: Testa relacionamento usuário-tarefas

### ❌ Error Handling
- **404 Errors**: Testa recursos inexistentes
- **Invalid Endpoints**: Valida tratamento de erros

## 🔍 Validações Implementadas

### ✅ Validações Básicas
- **Status Codes**: 200, 201, 404 conforme esperado
- **Response Time**: Máximo de 1000ms para operações
- **Content-Type**: Verificação de headers JSON
- **Campos Obrigatórios**: Presença de propriedades essenciais

### 🔧 Validações Avançadas
- **Schema Validation**: Usando biblioteca `tv4` integrada
- **Data Types**: Validação de tipos (string, number, boolean)
- **Format Validation**: Emails, URLs, estruturas complexas
- **Relationship Validation**: IDs de relacionamento corretos

### 📊 Validações de Negócio
- **Array Lengths**: Quantidade esperada de itens
- **Data Integrity**: Consistência entre recursos relacionados
- **Field Constraints**: Valores mínimos, formatos específicos

## 🎯 Validação de Contratos (Schema Validation)

### Implementação
A validação de schema é implementada diretamente nos scripts de teste do Postman usando a biblioteca `tv4` (Tiny Validator for JSON Schema v4).

### Schemas Definidos
- **Post Schema**: Valida estrutura de posts
- **User Schema**: Valida dados completos do usuário
- **Comment Schema**: Valida estrutura de comentários

### Exemplo de Uso
```javascript
const schema = {
    \"type\": \"object\",
    \"properties\": {
        \"id\": {\"type\": \"number\"},
        \"title\": {\"type\": \"string\"},
        \"body\": {\"type\": \"string\"},
        \"userId\": {\"type\": \"number\"}
    },
    \"required\": [\"id\", \"title\", \"body\", \"userId\"]
};

pm.test(\"Schema is valid\", function () {
    const jsonData = pm.response.json();
    pm.expect(tv4.validate(jsonData, schema)).to.be.true;
});
```

## 📋 Variáveis de Ambiente

| Variável | Valor | Descrição |
|----------|-------|-----------|
| `base_url` | `https://jsonplaceholder.typicode.com` | URL base da API |
| `default_user_id` | `1` | ID padrão do usuário |
| `default_post_id` | `1` | ID padrão do post |
| `default_album_id` | `1` | ID padrão do álbum |
| `test_timeout` | `1000` | Timeout para testes (ms) |

## 📚 Documentação Embutida

A coleção inclui documentação embutida no Postman com:
- **Descrição de cada pasta**: Objetivo e contexto dos testes
- **Descrição de requests**: Detalhes sobre cada endpoint
- **Exemplos de uso**: Como executar e interpretar resultados
- **Variáveis documentadas**: Explicação de todas as variáveis utilizadas

### Acessando a Documentação
1. No Postman, clique na coleção "JSONPlaceholder Tests"
2. Clique na aba "Documentation"
3. Navegue pela documentação estruturada

## 🏆 Principais Destaques

### ✨ Organização
- **Estrutura hierárquica**: Pastas organizadas por recurso
- **Nomenclatura clara**: Nomes descritivos e padronizados
- **Separação de responsabilidades**: Cada pasta com propósito específico

### 🔬 Qualidade dos Testes
- **Cobertura abrangente**: Todos os endpoints principais cobertos
- **Validações múltiplas**: Múltiplas verificações por request
- **Casos de erro**: Testes para cenários de falha

### 🔧 Automação
- **Scripts reutilizáveis**: Lógica de teste consistente
- **Variáveis dinâmicas**: Dados compartilhados entre testes
- **Execução em lote**: Capacidade de executar toda a suíte

### 📈 Relatórios
- **Resultados detalhados**: Informações completas sobre cada teste
- **Métricas de performance**: Tempo de resposta e estatísticas
- **Exportação de dados**: Resultados exportáveis para análise

## 🛠️ Tecnologias e Ferramentas

- **Postman**: Ferramenta principal para testes de API
- **tv4**: Biblioteca para validação de schema JSON
- **JSONPlaceholder**: API pública para testes
- **JSON Schema**: Padrão para validação de contratos

## 📊 Estatísticas do Projeto

- **Total de Requests**: 20+ endpoints testados
- **Validações por Request**: 5-10 testes por endpoint
- **Cobertura de Recursos**: 6 recursos diferentes (Posts, Comments, Users, Albums, Photos, Todos)
- **Tipos de Operação**: GET, POST, PUT, DELETE
- **Cenários de Erro**: Validação de casos 404 e endpoints inválidos

## 🎓 Aprendizados e Boas Práticas

### ✅ Implementadas
- **Organização estruturada** de testes por recurso
- **Validação rigorosa** de contratos de API
- **Automação completa** com scripts JavaScript
- **Documentação integrada** no próprio Postman
- **Reutilização de código** com variáveis de ambiente
- **Tratamento de cenários de erro**

### 🔄 Processo de Desenvolvimento
1. **Análise da API**: Estudo da documentação JSONPlaceholder
2. **Planejamento**: Definição da estrutura de testes
3. **Implementação**: Criação dos requests e scripts
4. **Validação**: Teste e refinamento das validações
5. **Documentação**: Criação da documentação completa
6. **Versionamento**: Organização para colaboração

## 🤝 Contribuição

Este projeto foi desenvolvido como demonstração de habilidades em:
- **Testes de API automatizados**
- **Validação de contratos**
- **Organização de projetos de teste**
- **Documentação técnica**
- **Boas práticas de desenvolvimento**

## 📄 Licença

Este projeto está licenciado sob a [MIT License](LICENSE) - veja o arquivo de licença para mais detalhes.

## 👨‍💻 Autor

**Anthony Coelho**
- GitHub: [@anthonycdp](https://github.com/anthonycdp)
- LinkedIn: [Anthony Coelho](https://www.linkedin.com/in/anthonycoelhoqae/)
- Email: anthonycoelho.dp@hotmail.com

*QA Engineer especializado em testes de performance e automação*

## 🤝 Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para:
- Abrir issues para reportar bugs ou sugerir melhorias
- Criar pull requests para novas funcionalidades
- Melhorar a documentação

## ⭐ Apoie o Projeto

Se este projeto foi útil para você, considere dar uma estrela! ⭐

---

**Desenvolvido com foco em qualidade, organização e boas práticas de testes de API** 🚀