### Como configurar uma Estratégia de Envio para sua loja VTEX

Abaixo você encontrará um passo a passo para configurar uma estratégia de envio para sua loja na plataforma VTEX.

Além de configurar as regras de envio, mostraremos como verificar se a estratégia está funcionando corretamente e como automatizar esse processo via API.

#### O que é uma Estratégia de Envio?

Uma estratégia de envio define as regras que determinam como os produtos da sua loja serão entregues aos clientes, considerando transportadoras, docas (pontos de origem), prazos e custos. Na VTEX, você pode personalizar suas opções de envio com base em zonas geográficas, tipos de frete, ou mesmo transportadoras específicas.

A imagem abaixo mostra o conjunto das configurações de [**logística**](https://help.vtex.com/pt/tutorial/politica-de-envio--tutorials_140) que compõem a estratégia de envio:

![shipping_strategy_PT](https://images.ctfassets.net/alneenqid6w5/1LdEuL3gjF12uwFj4ya6OL/c60984b010b96980383798cffad3527f/shipping_strategy_PT.png)

#### Configurando a estratégia de envio
**Passo 1**: Criar política comercial

A **[política comercial](https://help.vtex.com/pt/tutorial/como-funciona-uma-politica-comercial--6Xef8PZiFm40kg2STrMkMV)** é usada na VTEX para agrupar configurações de catálogo, preços, promoções, inventário, logística, segmentação de clientes e pagamentos para diferentes canais de venda:

![enter image description here](https://github.com/user-attachments/assets/25819f37-9ce9-4d71-af62-59a097295927)

Para [**contratar políticas comerciais adicionais**](https://help.vtex.com/pt/tutorial/contratacao-de-politica-comercial-adicional--61vuFOw4yGh6nwSmkLJL1X), você deve solicitar através do [**suporte VTEX**](https://help.vtex.com/pt/support), escolhendo a opção **Comercial** e selecionando o tipo de solicitação como Criação de Política Comercial.

**Passo 2**: Configurar política de envio

A **política de envio** é um conjunto de regras e configurações que definem quais opções e condições de envio serão apresentadas aos clientes no checkout.

 1. No **VTEX Admin** vá para **Envio** > **Estratégia de Envio**:

![enter image description here](https://github.com/user-attachments/assets/f7158cb2-ef14-4e1f-956c-469002cf5ec2)

2. Clique em `Criar política de envio`;
3. Preencha os campos da tela [conforme este artigo](https://help.vtex.com/pt/tutorial/criar-uma-politica-de-envio--66rJO4LKBdyMJOH6Z3dsaT);
4. clique em `Salvar alterações`.

**Passo 3**: Configurar planilha de frete

A **planilha de frete** (ou tabela de frete) define os custos de envio com base em diferentes fatores, como o peso dos produtos, volume e região de destino. Essa configuração é essencial para garantir que o valor do frete seja calculado corretamente.

1. No **Admin VTEX**, acesse ****Envio > Estratégia de envio > Políticas de envio > Criar política de envio**:
2. Clique em `Download da planilha de exemplo` na seção **Upload de tarifas de envio**:

![enter image description here](https://github.com/user-attachments/assets/2ae8df19-c5a3-4fc0-a02c-b702c493e15a)

3. Preencha os campos da coluna [**conforme este artigo**](https://help.vtex.com/pt/tutorial/planilha-de-frete--tutorials_127).

**Passo 4**: Configurar uma doca

A **doca** representa o local de origem dos envios, como centros de distribuição ou armazéns. É necessário configurar uma ou mais docas para garantir que os cálculos de frete sejam feitos com base nos endereços de origem corretos.

1.  Dentro do módulo **Envio**, clique em **Docas**;
2.  Clique em **Criar doca**;    
3.  Preencha os campos [conforme este artigo](https://help.vtex.com/pt/tutorial/gerenciar-doca--7K3FultD8I2cuuA6iyGEiW#campos-de-cadastro);    
4.  Salve as configurações.

**Passo 5**: Configurar estoque

O **estoque** precisa ser configurado para que a plataforma saiba quais produtos estão disponíveis em cada doca. Isso garante que os cálculos de frete e prazos de entrega estejam alinhados com a disponibilidade dos produtos.

1. Dentro do módulo **Envio**, clique em **Estoques**;
2. Clique no botão **Criar estoque**;
3. Confira se o botão está como  **Ativo**  no canto superior direito. Caso não esteja, mude-o para  **Ativo**:
![enter image description here](https://github.com/user-attachments/assets/08ee3292-377d-4fcc-aa34-ac1c7a951823)

4. 1.  Preencha os [campos de cadastro](https://help.vtex.com/pt/tutorial/gerenciar-estoque--tutorials_137#campos-de-cadastro);
5. Clique no botão  `Salvar alterações`.

#### Testando a configuração de envio: simulando uma compra

O **[**Simulador de envio**](https://help.vtex.com/pt/tutorial/simulador-de-envio--tutorials_144)** está disponível no Admin VTEX para simular e analisar as opções de entrega disponíveis. A simulação verifica as condições de entrega dando ao lojista a capacidade de verificar disponibilidade de itens, formas de entrega, custos e prazos.

1. No Admin VTEX, acesse  **Envio > Estratégia de Envio**;
2. Clique em  `Simulador de envio`:

![enter image description here](https://github.com/user-attachments/assets/2744669c-0f8b-4cd6-82fe-6cba4394228f)

3. Preencha: o `País` e a `Política comercial` desejada;
4. Selecione: o `produto` (por nome ou ID) e a `quantidade` do SKU;
5. Determine o `Preço`. Este campo é aberto e opcional;
6. Clique no ícone `+` para adicionar mais de um produto na simulação. Se desejar, pode preencher o box `Simular itens individualmente`;
7. Digite o `Código postal` que deseja realizar a simulação;
8. Clique no botão `Calcular`.

Para mais informações e datalhes da simulação, [**confira este artigo**](https://help.vtex.com/pt/tutorial/simulador-de-envio--tutorials_144#detalhes-da-simulacao):

![enter image description here](https://github.com/user-attachments/assets/da202f8b-b7ca-4b69-8c07-285cba15fe0b)

#### Configurações via API

Caso deseje configurar a estratégia de envio via API, a VTEX disponibiliza endpoints específicos para cada etapa do processo logístico:

- [**Configurar Política de Envio via API**](https://developers.vtex.com/docs/api-reference/logistics-api#logistics-api-create-shipping-policy)
- [**Submeter Planilha de Frete via API**](https://developers.vtex.com/docs/api-reference/logistics-api#post-/api/logistics/pvt/configuration/freights/-carrierId-/values/update)
- [**Criar Doca via API**](https://developers.vtex.com/docs/api-reference/logistics-api#post-/api/logistics/pvt/configuration/docks) 
- [**Configurar Estoque via API**](https://developers.vtex.com/docs/api-reference/logistics-api#post-/api/logistics/pvt/configuration/warehouses)
