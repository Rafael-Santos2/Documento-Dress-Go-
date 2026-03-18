# Dress & Go

## Visão Geral
O Dress & Go é um sistema de gerenciamento para lojas de departamentos especializadas no varejo de moda. O projeto visa automatizar o controle de catálogo, estoque e usuários, eliminando processos manuais que geram erros na gestão e na disponibilidade de peças.

O sistema também permite que clientes realizem **reservas online**, com retirada e pagamento posterior na loja física.

---

## Problema Central
Atualmente, o controle de roupas e usuários é feito de forma manual e pouco integrada, resultando em:
- Falhas na atualização de estoque
- Dificuldade no controle de reservas
- Risco de vendas duplicadas de itens indisponíveis
- Falta de rastreabilidade de pedidos e movimentações

---

## Funcionalidades Principais

### Gestão de Usuários
- Cadastro e autenticação de usuários
- Perfis de acesso:
  - **Gerente**: acesso total ao sistema
  - **Vendedor**: criação de pedidos e atendimento ao cliente
  - **Estoquista**: gerenciamento de estoque
  - **Cliente**: reserva de produtos
- Controle de permissões (RBAC)

---

### Controle de Catálogo e Estoque
- Cadastro de produtos com:
  - Nome
  - Descrição
  - Categoria
  - Preço
- Controle de variações:
  - Tamanho
  - Cor
- Cada item possui um **SKU único**
- Controle de estoque com:
  - Quantidade disponível
  - Quantidade reservada
  - Quantidade vendida
- Atualização automática do estoque após:
  - Venda
  - Reserva
  - Cancelamento
- Histórico de movimentações de estoque

---

### Reservas (Online e Presencial)
- Cliente pode reservar produtos pelo site
- Requisitos:
  - Usuário autenticado
- Funcionalidades:
  - Criar reserva
  - Cancelar reserva
- Sistema define automaticamente:
  - Data de expiração da reserva (7 dias)
- Reserva:
  - Bloqueia a quantidade no estoque
- Notificação opcional (email ou sistema)

---

### Vendas e Pedidos
- Criação de pedidos com múltiplos itens
- Estados do pedido:
  - Criado
  - Reservado
  - Aguardando pagamento
  - Pago
  - Cancelado
  - Expirado
  - Finalizado
- Um pedido deve conter pelo menos um item

---

### Pagamentos
- Métodos suportados:
  - Cartão
  - Pix
  - Boleto
  - Dinheiro
  - Parcelamento
- Status do pagamento:
  - Pendente
  - Aprovado
  - Recusado
- Pagamento realizado preferencialmente na retirada (loja física)
- Possibilidade de integração futura com gateway de pagamento

---

### Relatórios
- Vendas por período
- Produtos mais vendidos
- Reservas expiradas
- Receita total
- Controle de desempenho da loja

---

## Regras de Negócio

- Um pedido deve conter pelo menos um item
- A forma de pagamento é obrigatória para conclusão da venda
- Reservas:
  - Expiram automaticamente após 7 dias
  - Devem bloquear a quantidade correspondente no estoque
- Um produto pode ter múltiplas reservas **desde que haja estoque disponível**
- O sistema deve impedir venda/reserva acima da quantidade disponível
- Cancelamento de reserva:
  - Libera o estoque automaticamente

---

## Processos Automáticos

- Execução periódica para:
  - Cancelar reservas expiradas
  - Atualizar status de pedidos expirados
  - Liberar estoque automaticamente
- Implementação via scheduler

---

## Controle de Concorrência

- Uso de transações no banco de dados
- Controle para evitar:
  - Dupla reserva do mesmo item
  - Venda simultânea inconsistente

---

## Requisitos Técnicos

### Arquitetura
- Backend em Java
- API REST para comunicação entre frontend e backend

---

### Persistência
- Banco de dados relacional
- Entidades principais:
  - User
  - Product
  - InventoryItem
  - Order
  - OrderItem
  - Reservation
  - Payment

---

### Segurança
- Senhas armazenadas com hash
- Comunicação via HTTPS
- Autenticação
- Controle de acesso baseado em perfil

---

### Interface
- Interface desktop responsiva
- Separação de módulos:
  - Área administrativa
  - Área do cliente

---

### API (Exemplos de Endpoints)
- `/users`
- `/products`
- `/inventory`
- `/orders`
- `/reservations`
- `/payments`

---

### Validação e Tratamento de Erros
- Validação de dados de entrada
- Mensagens de erro padronizadas
- Sistema de logs para auditoria

---

### Testes
- Testes unitários
- Testes de integração

---

## Casos de Uso (Exemplos)

- Cliente realiza reserva online
- Cliente cancela reserva
- Vendedor cria e finaliza um pedido
- Estoquista atualiza estoque
- Sistema cancela automaticamente reservas expiradas
- Gerente visualiza relatórios de vendas
