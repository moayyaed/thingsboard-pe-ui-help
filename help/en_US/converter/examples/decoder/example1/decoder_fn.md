#### Decoder example JavaScript function

```javascript
{:code-style="max-height: 500px;"}
// Decode an uplink message from a buffer
// payload - array of bytes
// metadata - key/value object

/** Decoder **/

// decode payload to JSON
var json = decodeToJson(payload);

var timestamp = Date.parse(json.ts);
// Result object with device/asset attributes/telemetry data
var result = {
// Use deviceName and deviceType or assetName and assetType, but not both.
    deviceName: json.serialNumber,
    deviceType: "Thermostat",
    telemetry: {
        ts: timestamp,
        values: {
            temperature: json.t,
            humidity: json.h,
        }
    }
};

/** Helper functions **/

function decodeToString(payload) {
    return String.fromCharCode.apply(String, payload);
}

function decodeToJson(payload) {
    // covert payload to string.
    var str = decodeToString(payload);

    // parse string to JSON
    var data = JSON.parse(str);
    return data;
}

return result;
{:copy-code}
```

<br>
<br>
