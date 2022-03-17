---
date_added: 2021-07-27
model: ZM-CG205
vendor: Tuya
title: Door Magnetic Sensor
category: sensor
supports: contact, battery, tamper
mlink: 
link: https://www.aliexpress.com/item/1005002440470114.html 
link2: https://www.aliexpress.com/item/1005002512326796.html
zigbeemodel: ['TS0203', '_TYZB01_xph99wvr','_TYZB01_ncdapbwy']
compatible: [deconz,z2m]
---

## Pairing
6 Second press to connect via pen-hole. Connects to Tuya and Lidl Zigbee3 Gateways. Is found by deCONZ but not recognized (yet).  

For deCONZ, edit DDF:

```
{
  "schema": "devcap1.schema.json",
  "manufacturername": "_TZ3000_26fmupbb",
  "modelid": "TS0203",
  "product": "TS0203",
  "sleeper": true,
  "status": "Gold",
  "path": "/devices/ts0203.json",
  "subdevices": [
    {
      "type": "$TYPE_OPEN_CLOSE_SENSOR",
      "restapi": "/sensors",
      "uuid": [
        "$address.ext",
        "0x01",
        "0x0500"
      ],
      "fingerprint": {
        "profile": "0x0104",
        "device": "0x0402",
        "endpoint": "0x01",
        "in": [
          "0x0000",
          "0x0001",
          "0x0500"
        ]
      },
      "items": [
        {
          "name": "attr/id"
        },
        {
          "name": "attr/lastannounced"
        },
        {
          "name": "attr/lastseen"
        },
        {
          "name": "attr/manufacturername"
        },
        {
          "name": "attr/modelid"
        },
        {
          "name": "attr/name"
        },
        {
          "name": "attr/swversion"
        },
        {
          "name": "attr/type"
        },
        {
          "name": "attr/uniqueid"
        },
        {
          "name": "config/battery",
          "parse": {
            "fn": "None"
          }
        },
        {
          "name": "config/enrolled",
          "public": false,
          "description": "State of IAS enrollment process."
        },
        {
          "name": "config/on"
        },
        {
          "name": "config/pending",
          "description": "Pending tasks to configure the device."
        },
        {
          "name": "config/reachable"
        },
        {
          "name": "state/lastupdated"
        },
        {
          "name": "state/lowbattery",
          "description": "True when the device battery runs low."
        },
        {
          "name": "state/open",
          "awake": true,
          "read": {
            "fn": "None"
          },
          "parse": {
            "at": "0x0002",
            "cl": "0x0500",
            "ep": 1,
            "eval": "Item.val = (Attr.val & 0x3) != 0",
            "fn": "zcl"
          }
        },
        {
          "name": "state/tampered"
        }
      ]
    }
  ],
  "bindings": [
    {
      "bind": "unicast",
      "src.ep": 1,
      "cl": "0x0001",
      "report": [
        {
          "at": "0x0021",
          "dt": "0x20",
          "min": 300,
          "max": 3600,
          "change": "0x00000001"
        }
      ]
    },
    {
      "bind": "unicast",
      "src.ep": 1,
      "cl": "0x0500",
      "report": [
        {
          "at": "0x0002",
          "dt": "0x19",
          "min": 300,
          "max": 3600
        }
      ]
    }
  ]
}
```
