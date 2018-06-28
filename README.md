---
description: API Document123456
---

# API Document for Developer

## Integrations

### Get all devices

Returns all devices in the enterprise.

#### Request

`[PlatformAddress]/api/connector/v1/devices/getAll`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D"
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |

#### Response

```javascript
{
    "Devices": [
        {
            "Id": "d14efcfd-75b9-4bd3-9f10-5657a01f860a",
            "Name": "Key cutter 1",
            "Type": "KeyCutter"
        }
    ]
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Devices` | array of [Device](https://github.com/vmpatel-cygnet/TestGitBook/tree/701dab76e666dcbb27f509d2d30842d4254bef75/integrations.md#device) | required | The devices. |

**Device**

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Id` | string | required | Unique identifier of the device. |
| `Name` | string | required | Name of the device. |
| `Type` | string | required | Type of the device \(see [Command data](https://github.com/vmpatel-cygnet/TestGitBook/tree/701dab76e666dcbb27f509d2d30842d4254bef75/integrations.md#command-data)\). |

### 

