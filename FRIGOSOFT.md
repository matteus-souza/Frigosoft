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


---
---

991728081


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

![alt text](image-4.png)


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
