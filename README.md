# relacional-e-commerce
Modelo de Banco de Dados relacional de um sistema de e-commerce 

 1. Tabela Users (Usuários)
Essa tabela armazena as informações dos clientes que utilizam o e-commerce.

Campo	Descrição
user_id	Identificador único do usuário (Chave Primária).
name	Nome do usuário.
email	Endereço de e-mail (deve ser único para cada usuário).
password	Senha do usuário (armazenada de forma segura, idealmente criptografada).
address	Endereço de entrega do usuário.
✅ Relacionamento:

Um usuário pode fazer vários pedidos (relação 1:N com a tabela Orders).
📌 2. Tabela Products (Produtos)
Guarda as informações dos produtos disponíveis para compra no e-commerce.

Campo	Descrição
product_id	Identificador único do produto (Chave Primária).
name	Nome do produto.
description	Descrição detalhada do produto.
price	Preço do produto.
stock_quantity	Quantidade em estoque disponível.
category_id	Chave estrangeira que referencia a tabela Categories.
✅ Relacionamento:

Cada produto pertence a uma categoria (N:1 com a tabela Categories).
Um produto pode estar em vários pedidos (N:N com a tabela Orders, intermediado pela tabela Order_Items).
📌 3. Tabela Categories (Categorias)
Organiza os produtos em diferentes categorias.

Campo	Descrição
category_id	Identificador único da categoria (Chave Primária).
category_name	Nome da categoria (ex.: Eletrônicos, Roupas, etc.).
✅ Relacionamento:

Uma categoria pode conter vários produtos (1:N com a tabela Products).
📌 4. Tabela Orders (Pedidos)
Registra os pedidos realizados pelos usuários.

Campo	Descrição
order_id	Identificador único do pedido (Chave Primária).
user_id	Chave estrangeira que referencia o cliente (da tabela Users).
order_date	Data em que o pedido foi realizado.
total_amount	Valor total do pedido.
status	Status do pedido (ex.: Pendente, Enviado, Concluído).
✅ Relacionamento:

Cada pedido pertence a um usuário (N:1 com Users).
Um pedido pode conter vários produtos (N:N com Products através de Order_Items).
Cada pedido tem um pagamento associado (1:1 com Payments).
📌 5. Tabela Order_Items (Itens do Pedido)
Tabela intermediária que vincula os pedidos aos produtos. Resolve a relação N:N entre Orders e Products.

Campo	Descrição
order_item_id	Identificador único do item do pedido (Chave Primária).
order_id	Chave estrangeira que referencia o pedido (da tabela Orders).
product_id	Chave estrangeira que referencia o produto (da tabela Products).
quantity	Quantidade do produto nesse pedido.
price_per_item	Preço do produto no momento da compra.
✅ Relacionamento:

Conecta cada pedido a múltiplos produtos e vice-versa.
📌 6. Tabela Payments (Pagamentos)
Armazena as informações de pagamento dos pedidos.

Campo	Descrição
payment_id	Identificador único do pagamento (Chave Primária).
order_id	Chave estrangeira que referencia o pedido (da tabela Orders).
payment_method	Método de pagamento (ex.: Cartão de Crédito, Boleto, PIX).
payment_status	Status do pagamento (ex.: Aprovado, Pendente, Cancelado).
amount	Valor pago.
✅ Relacionamento:

Cada pedido tem um pagamento (1:1 com Orders).
📊 Resumo dos Relacionamentos
Users ↔ Orders: 1:N (Um usuário pode fazer vários pedidos).
Orders ↔ Order_Items ↔ Products: N:N (Um pedido contém vários produtos, e um produto pode estar em vários pedidos).
Products ↔ Categories: N:1 (Cada produto pertence a uma categoria).
Orders ↔ Payments: 1:1 (Cada pedido tem um único pagamento associado).
