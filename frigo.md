#  PASSO 1: Contrato

- 'ERP'
- Módulo frigorifico
  - Contrato de compra de animais

![alt text](image-8.png)
# PASSO 2: Recebimento c/ escala ( EAS = Escala de abate Dif )

- Frigosoft
  - Bovinos
    - Recebimentos de Animais

![alt text](image-36.png)
- Rec s/ carga
  - Vou incluir a placa do caminhão, motorista ...
- Cargas
  - Selecionar a carga
- Pesar ou Digitar o peso
  - Informar o peso da carga o lote e quantidade de animais
- Romaneio 
  - (Criar escalas)
- Voltar ao menu principal do frigosoft
  - Bovinos
    - Pesagem para abate 
      - (Iniciar)



# PASSO 3: Rast 1
  - Coletor
    - Abate
     - Rastreamento 01

![alt text](image-37.png)
![alt text](image-47.png)

# PASSO 4: Tipificação

  - Coletor
    - Abate
     - Tipificação

![alt text](image-38.png)

# PASSO 5: Pesagem abate (RAA)

- Frigosoft
  - Bovinos
    - Pesagem do abate

![alt text](image-39.png)

---
- *OBS: TIRAR RELATÓRIOS*
---

 - *'ERP'*
   - *Módulo frigorifico*
        - *Relatórios de abate*
            - WRABT010
            - WRABT011

# PASSO 6: Endereçamento de carcaças

- Coletor
  - Endereçamento de carcaças

*OBS: STATUS TIPO 'C'*

  - DIANTEIRO 
  - TRASEIRO
  - PONTA DE AGULHA

![alt text](image-40.png)
![alt text](image-41.png)
- Informe o volume ou a sequência

---
- *OBS: TIRAR RELATÓRIOS*
---

 - *'ERP'*
   - *Módulo frigorifico*
        - *Relatórios de abate*
           - WRABT014


# PASSO 7: Criação de camara de endereçamento

- 'ERP'
  - Módulo WMS
    - Cadastro
      - Camara de estocagem

![alt text](image-42.png)



# Verificação no sql a tabela referente ao endereçamento da carcaça:

{ select localizacao, concat(cod_filial, serie_volume, num_volume) as VOLUME, cod_produto, peso_liquido, vol.status, vol.banda,  *  from tbSisBov sis 

inner join tbvolume vol on sis.id = vol.id_sisbov

where sis.Data_abate = '20250309'
and sis.Num_lote = '01' }

![alt text](image-43.png)

![alt text](image-44.png)

>![alt text](image-45.png)
>
> - E: MEIA CARCAÇA
> - E: MEIA CARCAÇA
> - C: TRASEIRO
> - C: TRASEIRO
> - C: DIANTEIRO
> - C: DIANTEIRO
> - C: PONTA DE AGULHA
> - C: PONTA DE AGULHA

# PASSO 8: ACERTO PRODUTOR:

- 'ERP'
  - Módulo frigorifico
  - Preço acerto de produtor
    - Selecionar o produtor a ser pago

![alt text](image-46.png)

# PASSO 9: ORDEM DE PRODUÇÃO - PRODUTO ACABADO

- 'ERP'
  - Módulo Industria
    - Ordem de produção - Produto acabado

![alt text](image-48.png)

*OBS: Esse campo deve ser informado para que a pesagem do item seja correta,
caso ele nao queira por nenhum valor minimo, colocar valor 0.

![alt text](image-49.png)

- Frigosoft
  - Bovinos
    - Apontamento de produto acabado (RPE)

O serviço deve iniciar automático, selecione o item, pese o item, e informe a quantidade que ira conter dentro da caixa.
enquanto a pesagem e a informação de cada caixa ele vai alimentando o estoque do item.

![alt text](image-51.png)

> - { Select * from tbVolume
> - where Data_producao = '20250410'
> - and Serie_volume = '200'}

![alt text](image-50.png)


# PASSO 10: PRODUÇÃO DE MIÚDOS

## 1 ) Ordem de produção:

- 'ERP'
 - Modulo Industria
  - Ordem de Produção - Produto acabado
    - Lista de ordem de produção
      - Novo

![alt text](image-54.png)

## 2 ) Apontamento de Produção:

- Frigosoft
  - Bovino
    - Apontamento de produto acabado 

![alt text](image-55.png)

## 3 ) Relatório de Abate / produção:

Esse relatorio tras a diferença entre o peso quente e o peso resfriado do item, informado quando feito a aspersão
'ERP'
 - Módulo frigorifico
   - Relatório de abate
     - Relatório 2
       - WRPRD012

![alt text](image-52.png)

Este relatório é para verificarmos quais os 'PH' foram medidos antes da aspersão.

 - Módulo frigorifico
   - Relatório de abate
     - Relatório 1
       - WRABT013

![alt text](image-53.png)

# PASSO 11: QUARTEIO

- Coletor
  - wms
    - Quarteio

{ select  Banda, Status, Cod_produto, CONCAT(cod_filial,Serie_volume, Num_volume) as volume, Peso_liquido, ID_meia_carcaca from tbvolume
where Data_producao = '20250410'
and Serie_volume = '500'
and Check_sum is null }

![alt text](image-56.png)

- Nessa parte estamos realizando o quarteio do animal, que seria a separação, da meia carcaça para:

- Dianteiro
- Traseiro
- Ponta de agulha

![alt text](image-57.png)

apos realizar o peso do quarteio ele da baixa automatico a meia carcaça e adiciona para as partes que foi pesada ( Dianteiro, Traseiro e ponta de agulha).

![alt text](image-58.png)

- Coloque o volume a ser quarteado
  - As costelas não faz o quarteio pq são armazenadas diferente

![alt text](image-59.png)


# PASSO 12: PALETIZAÇÃO DO QUARTEIO
 
- Coletor 
 - WMS
   - Criar pallet
     - 3 PONTOS
       - Add novo pallet

![alt text](image-60.png)

- Indique o volume

Ele irá somar cada costela ao pallet, indicando o peso total do pallet

Paletização PA (PONTA DE AGULHA)

![alt text](image-61.png)

# PASSO 14: PRODUÇÃO CARNE SEM OSSO:

![alt text](image-66.png)

> TIPOS DE MOVIMENTOS GERADOS POR ESSE PROCESSO:

RMP - Reserva de materia prima (Gera TMV T629)

RPS - Romaneio de produção de saida ( Dar a baixa na matereia prima T630 )

RPE - Romaneio de produção de entrada ( Ele que ira dar entrada no produto acabado T621 )

---

1 ) Ordem de produção ( ORP - T620) ( RMP)

'ERP'
 - Industria
   - Ordem de produção - Produto acabado

![alt text](image-62.png)

  - Novo
   - Complete as informaçoes necessarias

![alt text](image-63.png)

-  Add os itens 

![alt text](image-64.png)

- Previsão matéria prima
  - Coloque o item traseiro 
    - Coleque a rastreabilidade

![alt text](image-65.png)

- Coletor
  - Produção
    - Romaneio de saida RPS
      - Selecione o romaneio
       - Romanear

![alt text](image-67.png)


![alt text](image-68.png)


*OBS: RELATÓRIO PARA VERIFICAÇÃO DO ROMANEIO DE SAÍDA*

- Frigorifico
  - Relatórios 2
    - WRPRD002

![alt text](image-4.png)

# PASSO 15: CRIAÇÃO DE CAMARA DE ESTOCAGEM
- WMS
  - Camara de estocagem
    - Criar nova camara de estocagem

![alt text](image-70.png)

Essa parte é muito importante, é nela que iremos criar os porta pallet do cliente, entre niveis ruas e posições.

# PASSO 16: DEFINIÇÃO DE CAMARA

- WMS 
  - Definição de camara

![alt text](image-71.png)

    - Nessa parte vamos informar a onde sera a rua, a posição

# PASSO 17: PALLETIZAÇÃO SIMPLES

- Coletor
 - Palletização simples 
   - Add novo pallet
     - Insira o codigo do volume
      - Finalizar

![alt text](image-72.png)


# PASSO 18: ARMAZENAR PALLET

- Inserir o numero do pallet
  - Informe o endereço que o pallet sera guardado

![alt text](image-73.png)

# PASSO 19: EXPEDIÇÃO PELO SISATAK: PEDIDO DE VENDA

Para realizar essa função é necessario ter o cadastro de cliente mercado interno, lista de preço e item.

- SISATAK
  - MOV011
    - T500 (PEDIDO DE VENDA)
      - Informe o cliente mercado interno (TIPO C)

![alt text](image-75.png)

* OBS: Verifique a lista de preço, para o itens que esta relacionada para aquela lista

      - Add os itens que esta referenciado a lista de preço
      - Atualize o documento ele ira gerar o pedido de venda

*OBS: Caso ao atualizar o documento apareça uma mensagem informando que o pedido foi bloqueado por conta de limite, siga os seguintes passos para liberar o pedido

- SISATAK
  - Movimentação E/S
  - Desbloqueio de documentos
    - Selecione o pedidos que deseja liberar

### Tire o relatório para verificar se deu certo o processo

- Movimentação E/S
  - Relatório
    - WRMVS009

![alt text](image-74.png)

# PASSO 20: MONTAGEM DE CARGA

### PELO ERP
- 'ERP'
   - Montagem de carga
     - Buscar documentos

![alt text](image-76.png)

     - Salvar carga
     
### SISATAK

- Logistica
  - Montagem de carga
  - Informe a data da movimentação
  - Informe a rota
  - Informe o caminhão
  - Informe o motorista
  
![alt text](image-77.png)

  - Aba montagem de carga
    - Qunado mudar para essa aba, a carga precisa ser carregada automatica

![alt text](image-78.png)

  - De um duplo clique e selecione a sequencia da montagem
    - Atualize o documento


*OBS: Tire o relatório:
    - 'ERP'
      - Modulo Logistica
        - Relatório
        - WRVDA004

![alt text](image-79.png)

# PASSO 21: BIPAGEM DE CARGA

- Coletor
- Expedição
  - Expedição por carga

![alt text](image-80.png)

    - Selecione a carga
      - Selecione qual carga voce deseja bipar primeiro
      - Selecio qual item voce quer bipar a caixa
      - Informe o cod interno do volume (Bipar a caixa)
      - Apos informar todos os itens naquele romaneio
      - Atualizar o documento

![alt text](image-81.png)

### RELATÓRIO

- 'ERP'
  - Logistico
    - Relatório
      - WRVDA003

![alt text](image-82.png)

# PASSO 22: BALANÇÃO DE VENDA

- Frigosoft
  - Bovino
  - Balanção
    - Informe a placa do veículo
    - Informe o tipo do volume
    - Tipo de frete
    - Motorista
    - Transportador (Transportadora responsavel)
    - Item de carga
    - Pese o caminhão vazio
    - Pese o caminhão cheio
    - Salvar

![alt text](image-83.png)

**A principal função do balação é a comparação entre o peso inicial e final, indicando a diferença, que informa o 'valor' real da carga**

![alt text](image-84.png)



---
---

T500 = Pedido de venda
T510 = Romaneio de saida de mercadorias
T520 = Venda mercado interno

# ABATE 


Tipificação da carcaça:

Meia carcaça:

- 'ERP'
  - Módulo estoque
- Meia carcaça
  - Novo
    
![alt text](image-1.png)

- add o novo item 

![alt text](image.png)


---


![alt text](image-3.png)

![alt text](image-2.png)
- Ativar os quartos


## Passo 1:
# CONTRATO DE ABATE

DIA: 12/03

Realizado um dia antes do abate

- 'ERP'
  - Módulo Frigorifico
    - Contrato de compra de animais

![alt text](image-5.png)

- Novo

![alt text](image-6.png)

- Duplo clique no  'T200'

![alt text](image-11.png)

- Preencher os campos 
  - Participante
    - Cadastro 
      - Produtor
  - Dados da propriedade
    - Propriedade rural
  - Informações Gerais
    - Tipo do cadastro:
      - Peso morto

![alt text](image-8.png)

- Add um novo item

![alt text](image-9.png)

- Atualizar documento
- Concluir/ Atualizar

![alt text](image-12.png)

---
--- 

## Passo 2 

# Relatório 
![alt text](image-13.png)
![alt text](image-14.png)

## Passo 3  

# Recebimento de animais com ou sem escala: 

# COM ESCALA:

![alt text](image-15.png)
![alt text](image-16.png)
![alt text](image-17.png)
![alt text](image-18.png)
![alt text](image-19.png)
![alt text](image-20.png)
![alt text](image-21.png)
![alt text](image-22.png)
![alt text](image-23.png)
Relatório:
![alt text](image-24.png)

---

# CRIAR ROMANEIO:

![alt text](image-25.png)
![alt text](image-26.png)
![alt text](image-27.png)
![alt text](image-28.png)
![alt text](image-29.png)
![alt text](image-30.png)
![alt text](image-31.png)
![alt text](image-33.png)
![alt text](image-32.png)
![alt text](image-34.png)
![alt text](image-35.png)

# 
