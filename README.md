# CRUD de E-commerce (UNIPE CD)

## Estrutura do banco de dados

### Usuários
- ID, Nome, Email, Telefone, Endereço
- Timestamps (criação/atualização)

### Produtos
- ID, Nome, Descrição, Preço, Estoque, Categoria, SKU
- Status ativo/inativo

### Pedidos
- ID, Total, Status, Endereço de entrega
- Relacionamento com usuário

### Itens do Pedido
- Quantidade, Preço unitário
- Relacionamento com produto e pedido

## 🔗 Principais Endpoints

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| POST | `/users/` | Criar usuário |
| GET | `/users/` | Listar usuários |
| POST | `/products/` | Cadastrar produto |
| GET | `/products/` | Listar produtos |
| POST | `/orders/` | Criar pedido |
| GET | `/orders/` | Listar pedidos |
| PUT | `/orders/{id}/status` | Atualizar status |



### 1. Iniciar o Servidor
```bash
uvicorn main:app --reload
```

### 2. Abrir no Navegador
- **Documentação Interativa**: http://localhost:8000/docs
- **API Principal**: http://localhost:8000

### Criar Usuário
```bash
curl -X POST "http://localhost:8000/users/" \
-H "Content-Type: application/json" \
-d '{
  "name": "Felipe Honorato de Sousa",
  "email": "felipe@moises.ai",
  "phone": "+559888882123",
  "address": "UNIPE, 123"
}'
```

### Criar Produto
```bash
curl -X POST "http://localhost:8000/products/" \
-H "Content-Type: application/json" \
-d '{
  "name": "Smartphone",
  "description": "Smartphone Android",
  "price": 1200.00,
  "stock": 15,
  "category": "Eletrônicos",
  "sku": "SM001"
}'
```

### Listar Produtos
```bash
curl http://localhost:8000/products/
```

### Fazer Pedido
```bash
curl -X POST "http://localhost:8000/orders/" \
-H "Content-Type: application/json" \
-d '{
  "user_id": 1,
  "shipping_address": "UNIPE, 123",
  "items": [
    {
      "product_id": 1,
      "quantity": 2
    }
  ]
}'
```

### Atualizar Status do Pedido
```bash
curl -X PUT "http://localhost:8000/orders/1/status" \
-H "Content-Type: application/json" \
-d '{
  "status": "confirmed"
}'
```

## 🎬 Roteiro de Demonstração (5 minutos)

1. **Abrir documentação** em `/docs` (30s)
2. **Criar usuário** via interface ou curl (1 min)
3. **Criar produto** mostrando validação (1 min)
4. **Fazer pedido** e mostrar cálculo automático (1.5 min)
5. **Mostrar estoque** atualizado automaticamente (1 min)

## 💡 Pontos para Destacar

- ✅ **Interface automática** - FastAPI gera documentação sozinho
- ✅ **Validação automática** - Dados incorretos são rejeitados
- ✅ **Relacionamentos** - Pedidos conectam usuários e produtos
- ✅ **Regras de negócio** - Estoque é controlado automaticamente
- ✅ **Estrutura profissional** - Código organizado em módulos

1. **Documentação automática** em `/docs`
2. **Validação de dados** (mostrar erro proposital)
3. **Controle de estoque** (criar pedido e ver estoque diminuir)
4. **Estrutura do código** (mostrar separação em arquivos)
5. **Relacionamentos** (pedido com usuário e produtos)
