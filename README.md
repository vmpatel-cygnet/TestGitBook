---
description: API Document123456
---

# API Document for Developer

## Integrations

### Get all devices

Returns all devices in the enterprise.

#### Parameters

| perPage | The number of events to get in a single api call. | Must be an integer greater than 0 |
| --- | --- | --- |
| start | The starting result of the page. Note this is zero based \(i.e. sending start=0 will start from the first result.\)  | Must be an integer 0 or greater |

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

