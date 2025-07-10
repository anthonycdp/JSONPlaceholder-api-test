# Guia de Execução de Testes

## 📋 Pré-requisitos

- Postman instalado (versão 8.0 ou superior)
- Conexão com internet para acessar a API JSONPlaceholder
- Arquivos da coleção e ambiente importados no Postman

## 🚀 Execução Passo a Passo

### 1. Importação dos Arquivos

1. **Abra o Postman**
2. **Clique em "Import"** (botão no canto superior esquerdo)
3. **Selecione os arquivos**:
   - `jsonplaceholder-tests.postman_collection.json`
   - `jsonplaceholder-environment.postman_environment.json`
4. **Confirme a importação**

### 2. Configuração do Ambiente

1. **Selecione o ambiente**: "JSONPlaceholder Environment" no dropdown superior direito
2. **Verifique as variáveis**:
   - `base_url`: https://jsonplaceholder.typicode.com
   - `default_user_id`: 1
   - `default_post_id`: 1

### 3. Execução de Testes Individuais

#### Para testar um endpoint específico:
1. Navegue até a pasta desejada (ex: "Posts")
2. Clique no request desejado (ex: "GET All Posts")
3. Clique em "Send"
4. Visualize os resultados na aba "Test Results"

### 4. Execução da Coleção Completa

#### Para executar todos os testes:
1. **Clique no nome da coleção**: "JSONPlaceholder Tests"
2. **Clique em "Run Collection"**
3. **Configure as opções**:
   - Delay: 100ms (recomendado)
   - Iterations: 1
   - Data: Nenhum arquivo necessário
4. **Clique em "Run JSONPlaceholder Tests"**

## 📊 Interpretação dos Resultados

### ✅ Testes Bem-sucedidos
- **Status Verde**: Teste passou
- **Checkmark**: Validação confirmada
- **Tempo de Resposta**: Exibido em milissegundos

### ❌ Testes Falhados
- **Status Vermelho**: Teste falhou
- **Mensagem de Erro**: Detalhes do que falhou
- **Logs**: Informações técnicas do erro

### 📈 Métricas Importantes
- **Response Time**: Deve estar abaixo de 1000ms
- **Status Code**: Deve corresponder ao esperado
- **Pass Rate**: Porcentagem de testes aprovados

## 🔧 Solução de Problemas

### Problema: Timeout nos Testes
**Solução**: Aumentar o timeout nas configurações do Postman

### Problema: Variáveis Não Definidas
**Solução**: Verificar se o ambiente está selecionado corretamente

### Problema: Falha na Validação de Schema
**Solução**: Verificar se a biblioteca tv4 está disponível no Postman

## 📋 Checklist de Execução

- [ ] Arquivos importados corretamente
- [ ] Ambiente selecionado
- [ ] Variáveis configuradas
- [ ] Conexão com internet ativa
- [ ] Testes individuais executados
- [ ] Coleção completa executada
- [ ] Resultados analisados
- [ ] Relatório gerado (se necessário)

## 💡 Dicas Importantes

1. **Execute os testes em ordem**: Alguns testes dependem de dados gerados por outros
2. **Monitore o tempo de resposta**: APIs lentas podem indicar problemas
3. **Verifique os logs**: Sempre analise os detalhes dos testes falhados
4. **Documente problemas**: Registre qualquer comportamento inesperado
5. **Execute regularmente**: Testes automatizados são mais eficazes quando executados frequentemente