# Dress & Go

## Visao Geral
O Dress & Go e um sistema de gerenciamento para lojas de departamentos especializadas no varejo de moda. O projeto visa automatizar o controle de catalogo e usuarios, eliminando processos manuais que geram erros na gestao de estoque e na disponibilidade de pecas.

## Problema Central
Atualmente, o controle de roupas e usuarios e feito de forma manual e pouco integrada, resultando em falhas na atualizacao do estoque e dificuldades no acompanhamento de reservas.

## Funcionalidades Principais
* Gestao de Usuarios: Cadastro de clientes e perfis de acesso (Gerente, Vendedor e Estoquista).
* Controle de Catalogo: Cadastro, edicao e visualizacao de roupas com status de disponibilidade em tempo real.
* Reservas e Locacoes: Registro de agendamentos e solicitacoes de locacao de roupas disponiveis.
* Vendas e Pagamentos: Gerenciamento de pedidos com suporte a multiplas formas de pagamento (Cartao, Pix ou Boleto).

## Regras de Negocio
* Nao e permitida mais de uma reserva para o mesmo item.
* Um pedido deve conter pelo menos um item para ser finalizado.
* Itens reservados devem ser retirados em um prazo maximo de uma semana.
* A forma de pagamento e um campo obrigatorio para a conclusao da venda.

## Requisitos Tecnicos
* Interface: Design responsivo e modular para facilitar a manutencao.
* Seguranca: Criptografia ponta a ponta para dados sensiveis e backup automatico diario.
* Persistencia: Dados armazenados localmente com performance otimizada para listagens.

## Desenvolvedores
* Nicolas Henrique
* Rafael Araujo
* Victor Seraco

## Licenca
Este projeto é para fins academicos.
