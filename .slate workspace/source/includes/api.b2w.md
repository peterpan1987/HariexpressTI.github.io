# B2W Marketplace

## Attributes

###Create an attribute– POST / attributes

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
###Update an attribute  – PUT / atributes/{name}

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

## Categories

### List Categories – GET / categories

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/categories \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

### Create a category – POST / categories

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

### Update Category – PUT / categories/{code}

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

### Delete Category – DELETE / categories/{code}

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

## Freights

### Return the freights history – GET / freights

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/freights \ 
--header 'accept: application/json' \
--header 'content-type: application/json' \
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

## Orders

### List orders – GET / orders

```curl

curl --request GET \ 
--url ' https://api.skyhub.com.br/orders?per_page=100&page=2' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br '

```

### Returns a specific order – GET / orders/{code}

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/orders/Lojas Americanas-266580617301 \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br '

```

### Invoice – POST / orders/{code}/invoice

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

### Cancel an order – POST / orders/{code}/cancel

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

### Confirm Delivery – POST / orders/{code}/delivery

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

### Send delivery data – POST / orders/{code}/shipments

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

### Gets shipping label – GET / orders/{code}/shipments_labels

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/orders/Lojas Americanas-266065081401/shipment_labels \ 
--header 'accept: application/pdf' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \

```

### Transport exception – POST / orders/{code}/shipments_exception

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

## PLP

### List PLP’s – GET / shipments/b2w

```curl

curl --request GET \ 
--url ' https://api.skyhub.com.br/shipments/b2w/' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br '

```

### Grouping Orders in a PLP – POST / shipments/b2w

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

### Ungroup PLP – DELETE / shipments/b2w

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

### Recover PLP – PDF – GET / shipments/b2w/view?plp_id={CODE}

```curl

curl --request GET \ 
--url 'https://api.skyhub.com.br/shipments/b2w/view?plp_id=14' \ 
--header 'accept: application/pdf' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \

```

### Order list apt for grouping – GET /shipments/b2w/to_group

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/shipments/b2w/to_group \ 
--header 'accept: application/pdf' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \

```

## Products 

### Returns the products registered in the skyhub – GET / products

```curl

curl --request GET \ 
--url 'https://api.skyhub.com.br/products?page=1&per_page=100' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \

```

### Returns a specific product in the skyhub – GET / products/{sku}

```curl

curl --request GET \ 
--url ' https://api.skyhub.com.br/products/0927@wangxx' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh ' \ 
--header 'x-user-email: ti@hariexpress.com.br ' \

```

### Create a product in the SkyHub – POST / products

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

### Update a product in the skyhub – PUT / products/{sku}

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

### Delete a product in the Skyhub – DELETE / products/{sku}

```curl

curl --request DELETE \ 
--url https://api.skyhub.com.br/products/15077 \ 
--header 'accept: application/json' \ 
--header 'content-type: application/x-www-form-urlencoded' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'  \

```

### Create product variation in the Skyhub – POST / products/{sku}/variations

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

### Marketplaces URL – GET / products/urls

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/products/urls \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json ' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'  \

```

### CREATE A PRODUCT WITH PRICE VARIATION IN THE SKU – POST / products

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

## QUEUES 

### Receive a queue of orders – GET / queues/orders

```curl

curl --request GET \ 
--url https://api.skyhub.com.br/queues/orders \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json ' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'  \

```

### Remove a request from the queue – DELETE / queues/orders/{code}

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