# B2W Marketplace

Getting started to B2W API.

## Attributes

### [POST] Create an attribute – https://api.skyhub.com.br/attributes

```curl

curl --request POST \ 
--url https://api.skyhub.com.br/attributes \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \ 
--data {
  "attribute": {
    "name": "att_name",
    "label": "Atributo Exemplo",
    "options": [
      "foo",
      "foo",
      "foo"
    ]
  }
}

```

CREATES A NEW PRODUCT ATTRIBUTE

### [PUT] Update an attribute – https://api.skyhub.com.br/atributes/{name}

```curl

curl --request PUT \ 
--url https://api.skyhub.com.br/attributes/att_name \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \ 
--data {
  "attribute": {
    "name": "att_name",
    "label": "Atributo Exemplo",
    "options": [
      "foo",
      "foo",
      "foo"
    ]
  }
}

```

UPDATES AN EXISTING ATTRIBUTE

## Categories

### [GET] List Categories – https://api.skyhub.com.br/categories

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/categories \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

LISTS ALL CATEGORIES REGISTERED ON SKYHUB

### [POST] Create a category – https://api.skyhub.com.br/categories

```curl

curl --request POST \ 
--url https://api.skyhub.com.br/categories \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \
--data {
  "category": {
    "code": "category001",
    "name": "eletrónicos > celulares > fone de ouvido"
  }
}

```

CREATES A CATEGORY ON SKYHUB

### [PUT] Update Category – https://api.skyhub.com.br/categories/{code}

```curl

curl --request PUT \ 
--url https://api.skyhub.com.br/categories/category001 \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \ 
--data {
  "category": {
    "code": "category001",
    "name": "eletrónicos > celulares > fone de ouvido"
  }
}

```

UPDATES ONLY ONE CATEGORY ON SKYHUB BY THE CATEGORY CODE

### [DEL] Delete Category – https://api.skyhub.com.br/categories/{code}

```curl

curl --request DELETE \ 
--url https://api.skyhub.com.br/categories/category001 \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \
--data {
  "category": {
    "code": "category001",
    "name": "eletrónicos > celulares > fone de ouvido"
  }
}

```

DELETES ONLY ONE CATEGORY ON SKYHUB BY THE CATEGORY CODE

## Freights

### [GET] Return the freights history – https://api.skyhub.com.br/freights

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/freights \ 
--header 'accept: application/json' \
--header 'content-type: application/json' \
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

LISTS ALL FREIGHTS

## Orders

### [GET] List orders – https://api.skyhub.com.br/orders

```curl

curl --request GET \ 
--url ' https://api.skyhub.com.br/orders?per_page=100&page=2' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br '

```

LISTS ALL ORDERS REGISTERED ON SKYHUB

### [GET] Returns a specific order – https://api.skyhub.com.br/orders/{code}

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/orders/Lojas Americanas-266580617301 \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br '

```

RETURNS ONLY ONE ORDER 

### [POST] Invoice – https://api.skyhub.com.br/orders/{code}/invoice

```curl

curl --request POST \ 
--url https://api.skyhub.com.br/orders/Lojas Americanas-266065081401/invoice\ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \
--data {
  "status": "payment_received",
  "invoice": {
    "key": "99999999999999999999999999999999999999999999"
  }
}

```

UPDATES AN ORDER WITH INVOICE INFORMATION

### [POST] Cancel an order – https://api.skyhub.com.br/orders/{code}/cancel

```curl

curl --request POST \ 
--url https://api.skyhub.com.br/orders/Lojas Americanas-266065081401/cancel \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \
--data {
  "status": "order_canceled"
}

```

UPDATES AN ORDER WITH THE CANCELATION DATA

### [POST] Confirm Delivery – https://api.skyhub.com.br/orders/{code}/delivery

```curl

curl --request POST \ 
--url https://api.skyhub.com.br/orders/Lojas Americanas-266065081401/delivery \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \
--data {
  "status": "complete"
}

```

UPDATES AN ORDER AS DELIVERED ON SKYHUB

### [POST] Send delivery data – https://api.skyhub.com.br/orders/{code}/shipments

```curl

curl --request POST \ 
--url https://api.skyhub.com.br/orders/Lojas Americanas-266065081401/shipments \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \
--data {
  "status": "order_shipped",
  "shipment": {
    "code": "Lojas Americanas-266065081401",
    "items": [
      {
        "sku": "foo",
        "qty": 1
      }
    ],
    "track": {
      "code": "BR1321830198302DR",
      "carrier": "Correios",
      "method": "SEDEX",
      "url": "www.correios.com.br"
    }
  }
}

```

UPDATES AN ORDER WITH THE TRACKING CODE DATA AND THE METHOD OF SHIPPING OF THE TRANSPORTER. (B2W accepts at maximum 200 characters in the URL of tracking).

### [GET] Gets shipping label – https://api.skyhub.com.br/orders/{code}/shipments_labels

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/orders/Lojas Americanas-266065081401/shipment_labels \ 
--header 'accept: application/pdf' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \

```

OBTAINS THE LABEL OF AN ORDER THAT HAD THE FREIGHT CALCULATED VIA B2W DELIVERIES

### [POST] Transport exception – https://api.skyhub.com.br/orders/{code}/shipments_exception

```curl

curl --request POST \ 
--url https://api.skyhub.com.br/orders/Lojas Americanas-266065081401/shipment_exception \ 
--header 'accept: application/pdf' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \
--data {
  "shipment_exception": {
    "occurrence_date": "2012-10-06T04:13:00-03:00",
    "observation": "Observação da Exceção de transporte"
  }
}

```

TRANSPORT EXCEPTION

## PLP

### [GET] List PLP’s – https://api.skyhub.com.br/shipments/b2w

```curl

curl --request GET \ 
--url ' https://api.skyhub.com.br/shipments/b2w/' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br '

```

FUNCTION THAT ALLOWS TO CHECK IN THE API ALL GROUPED PLPs. IN THE RETURN IT WILL BE POSSIBLE TO VERIFY THE ID OF THE PLP AND THE INSERTED ORDERS IN EACH GROUP.

### [POST] Grouping Orders in a PLP – https://api.skyhub.com.br/shipments/b2w

```curl

curl --request POST \ 
--url https://api.skyhub.com.br/shipments/b2w/ \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \
--data {
  "order_remote_codes": [
    "265358194401",
    "265358194401",
    "265358194401"
  ]
}

```

RETURN ORDERS TO GROUP, JUST 20 ORDERS FOR PAGE

### [DEL] Ungroup PLP – https://api.skyhub.com.br/shipments/b2w

```curl

curl --request DELETE \ 
--url https://api.skyhub.com.br/shipments/b2w/ \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \
--data {
  "plp_id": "14"
}

```

BASICALLY THE OPPOSITE OF THAT LAST OPERATION

### [GET] Recover PLP PDF – https://api.skyhub.com.br/shipments/b2w/view?plp_id={CODE}

```curl

curl --request GET \ 
--url 'https://api.skyhub.com.br/shipments/b2w/view?plp_id=14' \ 
--header 'accept: application/pdf' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \

```

FIRST YOU NEED TO GROUP THE PLPs, YOU WILL RECEIVE A ID AND USE IT IN THIS FUCTION. IF YOU WANT TO RECEIVE THE DATAS IN JSON FORMAT JUST USE THE HEADER Accept: application/json. 

### [GET] Order list apt for grouping – https://api.skyhub.com.br/shipments/b2w/to_group

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/shipments/b2w/to_group \ 
--header 'accept: application/pdf' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \

```

RETURN THE PLP ID, WITH THE ID WILL BE NECESSARY RECOVER THE PLP

## Products 

### [GET] Returns the products registered in the skyhub – https://api.skyhub.com.br/products

```curl

curl --request GET \ 
--url 'https://api.skyhub.com.br/products?page=1&per_page=100' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \

```

LIST ALL PRODUCTS REGISTERED ON SKYHUB

### [GET] Returns a specific product in the skyhub – https://api.skyhub.com.br/products/{sku}

```curl

curl --request GET \ 
--url ' https://api.skyhub.com.br/products/0927@wangxx' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \

```

GET ONLY ONE PRODUCT ACCORDING WITH THE SKU ID

### [POST] Create a product in the SkyHub – https://api.skyhub.com.br/products

```curl

curl --request POST \ 
--url https://api.skyhub.com.br/products \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \ 
--data {
  "product": {
            "sku": "15077",
            "name": "Fonte De Alimentação Digital Tipo Yihua - Yaxun Ps-1502dd - 130V",
            "description": "Ideal para a manutenção em equipamentos eletrônicos!<br/>Proporciona tranquilidade e precisão a seu usuário.<br/>Possui display duplo para controle de tensão e corrente Knob para ajuste da corrente de proteção.<br/>Um Knob com tensões pré-determinadas com cinco invariáveis e uma variável<br/>Proteção contra sobrecarga.<br/>Proteção contra inversão de polaridade.<br/>Refrigerado por dissipador.<br/>Sistema de segurança com corte de alimentação automático.<br/>Quando a corrente atinge seu pico, a fonte corta sua alimentação.<br/>A Fonte de Alimentação PS-1502DD é uma peça indispensável na bancada de quem deseja trabalhar corretamente sem necessidade de improvisos ou invenções na hora de reparar seus equipamentos.<br/>Além de ser um produto de alta precisão que fornece alimentação contínua, é também, muito leve e robusta, sendo muito prática e durável para os reparos do dia a dia.<br/>Conta ainda com sistema de segurança, um tipo de sistema que possibilita a fonte controlar a corrente máxima que deve fornecer, possibilitando ajustes entre 0.6 e 2A.<br/>uando o limite estipulado for alcançando a fonte corta automaticamente a alimentação para evitar a ocorrência de danos aos equipamentos que estão sendo testados.<br/>A fonte vem equipada com dois displays digitais de LED, o da esquerda indicada a corrente de proteção e a corrente de consumo, enquanto o da direita demonstra tensão ajustada.<br/>Para sua regulagem, ela conta com 4 Knobs de ajuste (potenciômetros) que lhe auxiliam no perfeito ajuste de tensão e corrente que circula até o seu equipamento.<br/>",
            "status": "enabled",
            "removed": false,
            "price": 255555,
            "promotional_price": 1690.90,
            "cost": null,
            "weight": 1.6,
            "height": 25,
            "width": 13,
            "length": 20,
            "brand": "Yaxun",
            "ean": null,
            "nbm": "84733011",
            "categories": [
                {
                    "code": "MLB30167",
                    "name": "Agro, Indústria e Comércio > Agro, Indústria e Comércio > Indústria Agrícola > Matéria Prima > Mudas"
                }
            ],
            "images": [
                "http://loja.multtechinfo.com.br/imagenslw/SB1_1515243081944.jpg",
                "https://www.bluecell.com.br/image/cache/catalog/foun160-600x600.jpg",
                "https://static3.tcdn.com.br/img/img_prod/375576/carregador_fonte_parede_maxx_733_3_usb_pmcell_qualcomm_3_0_9622_2_20170908094039.jpg"
            ],
            "specifications": [
                {
                    "key": "VOLTAGEM",
                    "value": "220v"
                }
            ],
            "variations": [
                {
                    "sku": "F0011-220",
                    "qty": 500,
                    "ean": "6959745160286",
                    "images": [
                      "http://loja.multtechinfo.com.br/imagenslw/SB1_1515243081944.jpg",
                "https://www.bluecell.com.br/image/cache/catalog/foun160-600x600.jpg",
                "https://static3.tcdn.com.br/img/img_prod/375576/carregador_fonte_parede_maxx_733_3_usb_pmcell_qualcomm_3_0_9622_2_20170908094039.jpg"
                    ],
                    "specifications": [
                        {
                            "key": "VOLTAGEM",
                            "value": "220v"
                        }
                    ]
                }
            ],
            "variation_attributes": [
              "VOLTAGEM"
            ]
  }
}

```

CREATES A PRODUCT, THE DETAILS GOES ON THE BODY (B2W accepts up to 25 characters in sku)

### [PUT] Update a product in the skyhub – https://api.skyhub.com.br/products/{sku}

```curl

curl --request PUT \ 
--url https://api.skyhub.com.br/products/B2W15233202767811 \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \ 
--data {
    "product": {
        
        "status": "enabled",
        "removed": false,
        "price": 255555,
        "promotional_price": 1690.9,
        "cost": null,
        "weight": 1.6,
        "height": 25,
        "width": 13,
        "length": 20,
        "brand": "Yaxun",
        "ean": null,
        "nbm": "84733011",
        "categories": [
            {
                "code": "MLB30167",
                "name": "Agro, Indústria e Comércio > Agro, Indústria e Comércio > Indústria Agrícola > Matéria Prima > Mudas"
            }
        ],
        "images": [
            "http://loja.multtechinfo.com.br/imagenslw/SB1_1515243081944.jpg",
            "https://www.bluecell.com.br/image/cache/catalog/foun160-600x600.jpg",
            "https://static3.tcdn.com.br/img/img_prod/375576/carregador_fonte_parede_maxx_733_3_usb_pmcell_qualcomm_3_0_9622_2_20170908094039.jpg"
        ],
        "specifications": [
            {
                "key": "Model",
                "value": "110V"
            },
            {
                "key": "wang'x'x",
                "value": "test4"
            },
            {
                "key": "huba",
                "value": "huba"
            }
        ],
        "variations": [
            {
                "sku": "F0011-220",
                "qty": 500,
                "ean": "6959745160286",
                "images": [
                    "http://loja.multtechinfo.com.br/imagenslw/SB1_1515243081944.jpg",
                    "https://www.bluecell.com.br/image/cache/catalog/foun160-600x600.jpg",
                    "https://static3.tcdn.com.br/img/img_prod/375576/carregador_fonte_parede_maxx_733_3_usb_pmcell_qualcomm_3_0_9622_2_20170908094039.jpg"
                ],
                "specifications": [
                    {
                        "key": "Size",
                        "value": "220v"
                    },
                    {
                        "key": "Total",
                        "value": "220V"
                    }
                ]
            },
            {
                "sku": "F0011-110",
                "qty": 200,
                "ean": "6959745160286",
                "images": [
                    "http://loja.multtechinfo.com.br/imagenslw/SB1_1515243081944.jpg",
                    "https://www.bluecell.com.br/image/cache/catalog/foun160-600x600.jpg",
                    "https://static3.tcdn.com.br/img/img_prod/375576/carregador_fonte_parede_maxx_733_3_usb_pmcell_qualcomm_3_0_9622_2_20170908094039.jpg"
                ],
                "specifications": [
                    {
                        "key": "Size",
                        "value": "110v"
                    },
                    {
                        "key": "Total",
                        "value": "110V"
                    }
                ]
            }
        ],
        "variation_attributes": [
            "Size",
            "Total"
        ]
    }
}

```

UPDATES A PRODUCT USING THE SKU ID

### [DEL] Delete a product in the Skyhub – https://api.skyhub.com.br/products/{sku}

```curl

curl --request DELETE \ 
--url https://api.skyhub.com.br/products/15077 \ 
--header 'accept: application/json' \ 
--header 'content-type: application/x-www-form-urlencoded' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'  \

```

DELETES A PRODUCT ON SKYHUB USING THE SKU ID

### [POST] Create product variation in the Skyhub – https://api.skyhub.com.br/products/{sku}/variations

```curl

curl --request POST \ 
--url https://api.skyhub.com.br/products/15077/variations \ 
--header 'accept: application/json' \ 
--header 'content-type: application/x-www-form-urlencoded' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'  \
--data {
  "variation": {
    "sku": "9932",
    "qty": 10,
    "ean": "foo",
    "images": [
      "foo",
      "foo",
      "foo"
    ],
    "specifications": [
      {
        "key": "Tamanho",
        "value": "1.00 M"
      }
    ]
  }
}

```

CREATES PRODUCTS VARIATION USING THE SKU ID

### [GET] Marketplaces URL – https://api.skyhub.com.br/products/urls

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/products/urls \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json ' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'  \

```

RETURNS THE URL OF THE PRODUCTS IN THE MARKETPLACES (B2W AND CNOVA)

### [POST] CREATE A PRODUCT WITH PRICE VARIATION IN THE SKU – https://api.skyhub.com.br/products

```curl

curl --request POST \ 
--url https://api.skyhub.com.br/products \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \ 
--data {
  "product": {
    "sku": "Skyhub",
    "name": "CRIAR PRODUTO COM MAIS DE UMA VARIAÇÃO",
    "description": "CRIAR PRODUTO COM MAIS DE UMA VARIAÇÃO",
    "status": "enabled",
    "price": 0.0,
    "promotional_price": 255,
    "cost": 0.2,
    "weight": 1.1,
    "height": 20,
    "width": 30,
    "length": 20,
    "brand": "SKYHUB",
    "nbm": "98769898",
    "categories": [
      {
        "code": "01",
        "name": "SKYHUB HOMOLOGAÇÃO"
      }
    ],
    "images": [
      "http://d26lpennugtm8s.cloudfront.net/stores/154/284/products/camiseta-lisa-verde-bandeira-algodo-p-ao-gg-pronta-entrega-355901-mlb20431777049_092015-o-07fadec89e5ed54705c1b9ab5411dec8-1024-1024.jpg",
      "http://d26lpennugtm8s.cloudfront.net/stores/154/284/products/camiseta-lisa-verde-bandeira-algodo-p-ao-gg-pronta-entrega-355901-mlb20431777049_092015-o-07fadec89e5ed54705c1b9ab5411dec8-1024-1024.jpg",
      "http://d26lpennugtm8s.cloudfront.net/stores/154/284/products/camiseta-lisa-verde-bandeira-algodo-p-ao-gg-pronta-entrega-355901-mlb20431777049_092015-o-07fadec89e5ed54705c1b9ab5411dec8-1024-1024.jpg"
    ],
    "specifications": [
      {
        "key": "Especicações do Produto PAI",
        "value": "Especificações do Produto PAI"
      }
    ],
    "variations": [
      {
        "sku": "301",
        "qty": 100,
        "ean": "9876543210987",
        "images": [
          "http://d26lpennugtm8s.cloudfront.net/stores/154/284/products/camiseta-lisa-verde-bandeira-algodo-p-ao-gg-pronta-entrega-355901-mlb20431777049_092015-o-07fadec89e5ed54705c1b9ab5411dec8-1024-1024.jpg",
          "http://d26lpennugtm8s.cloudfront.net/stores/154/284/products/camiseta-lisa-verde-bandeira-algodo-p-ao-gg-pronta-entrega-355901-mlb20431777049_092015-o-07fadec89e5ed54705c1b9ab5411dec8-1024-1024.jpg",
          "http://d26lpennugtm8s.cloudfront.net/stores/154/284/products/camiseta-lisa-verde-bandeira-algodo-p-ao-gg-pronta-entrega-355901-mlb20431777049_092015-o-07fadec89e5ed54705c1b9ab5411dec8-1024-1024.jpg"
        ],
        "specifications": [
          {
            "key": "price",
            "value": "15.00"
          }
        ]
      }
    ],
    "variation_attributes": [
      "foo",
      "foo",
      "foo"
    ]
  }
}

```

CREATES A PRODUCT WITH PRICE VARIATION IN THE SKU

## QUEUES 

### [GET] Receive a queue of orders – https://api.skyhub.com.br/queues/orders

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/queues/orders \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json ' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'  \

```

RETRIEVES THE FIRST AVILABLE ORDER IN THE INTEGRATION QUEUE. AFTER PROCESSING THE ORDER, IT MUST BE REMOVED FROM THE INTEGRATION QUEUE WITHIN 5 MINUTES (OR IT WILL RETURN TO THE BEGINNING OF THE QUEUE).

### [DEL] Remove a request from the queue – https://api.skyhub.com.br/queues/orders/{code}

```curl

curl --request DELETE \ 
--url https://api.skyhub.com.br/queues/orders/Lojas Americanas-266065081401 \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json ' \ 
--header 'x-accountmanager-key: pmcell@2017 ' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \
--data {
  "shipment_exception": {
    "occurrence_date": "2012-10-06T04:13:00-03:00",
    "observation": "Observação da Exceção de transporte"
  }
}

```

REMOVES AN ORDER FROM THE INTEGRATION QUEUE