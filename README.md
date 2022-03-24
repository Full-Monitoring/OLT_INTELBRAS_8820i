# OLT GPON INTELBRAS 8820i

## 🚧 Atualizando para a versão de firmware 2.81

## ATIVE AS NOTIFICAÇÕES PARA FICAR LIGADO NAS NOVIDADES

![image](https://user-images.githubusercontent.com/23584038/132106564-72ab4986-3c8a-4074-9d0b-9bc77e5c9d80.png)

## ⚠️ versão de firmware da olt: 2.81 ⚠️

![image](https://user-images.githubusercontent.com/23584038/128234027-a7dff4e8-0073-4a24-a47e-f7d147b4a312.png)

## Zabbix Templates

- [Zabbix 5.0](contents/OLT_INTELBRAS_8820i_ONUs%20zabbix%205_0.xml)
- [Zabbix 5.4](contents/OLT_INTELBRAS_8820i_ONUs%20zabbix%205_4.xml)

## O que vai encontrar nesses templates?

- SISTEMA
  - UPTIME
  - MEMORIA RAM LIVRE
  - CPU
- STATUS DAS PORTAS
- GPON
  - STATUS DA GPON
  - CORRENTE
  - VOLTAGEM
  - CONTADOR DE ONU's POR PON
  - RX POWER
  - TX POWER
  - TEMPERATURA

[Video demo](/contents/demo.mp4)

[Dashboard](contents/grafana_dash_OLT_INTELBRAS_8820i.json)

## ZABBIX - TEMPLATE

> Dividi o Template em quatro. Para usar conforme a necessidade.

![image](https://user-images.githubusercontent.com/23584038/132104647-9a10ebe3-7e61-4314-ad9b-a80b87942411.png)

> O descoberta para analise de trafego filtra apenas as interfaces com status UP.

```js
discovery[{#NAME},1.3.6.1.4.1.26138.1.1.1.1.1.2, {#STATUS},1.3.6.1.2.1.2.2.1.8]
```

> Item discovery de ONU's. Busca se as ONU's estão autorizadas, online e qual é a PON.

```js
discovery[{#PON},1.3.6.1.4.1.26138.1.2.1.1.1.2, {#ACT},1.3.6.1.4.1.26138.1.2.1.1.1.5, {#REG}, 1.3.6.1.4.1.26138.1.2.1.1.1.4]
```

> Pré-processamento

![image](https://user-images.githubusercontent.com/23584038/132104637-16ef4efd-9108-498a-b0b9-34216717acb7.png)


> Contador de ONU's Provisionadas por PON.

```js
1.3.6.1.4.1.26138.1.4.1.1.1.56.9 = PON1
1.3.6.1.4.1.26138.1.4.1.1.1.56.10 = PON2
1.3.6.1.4.1.26138.1.4.1.1.1.56.11 = PON3
1.3.6.1.4.1.26138.1.4.1.1.1.56.12 = PON4
1.3.6.1.4.1.26138.1.4.1.1.1.56.13 = PON5
1.3.6.1.4.1.26138.1.4.1.1.1.56.14 = PON6
1.3.6.1.4.1.26138.1.4.1.1.1.56.15 = PON7
1.3.6.1.4.1.26138.1.4.1.1.1.56.16 = PON8
```

> Contador de ONU's Ativas por PON.

```js
1.3.6.1.4.1.26138.1.4.1.1.1.55.9 = PON1
1.3.6.1.4.1.26138.1.4.1.1.1.55.10 = PON2
1.3.6.1.4.1.26138.1.4.1.1.1.55.11 = PON3
1.3.6.1.4.1.26138.1.4.1.1.1.55.12 = PON4
1.3.6.1.4.1.26138.1.4.1.1.1.55.13 = PON5
1.3.6.1.4.1.26138.1.4.1.1.1.55.14 = PON6
1.3.6.1.4.1.26138.1.4.1.1.1.55.15 = PON7
1.3.6.1.4.1.26138.1.4.1.1.1.55.16 = PON8
...
```

![image](https://user-images.githubusercontent.com/23584038/132105625-24060a34-e00d-4880-8bc3-02b6eeb9cdd4.png)
