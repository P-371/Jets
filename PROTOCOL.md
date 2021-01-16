# Protocol

## Types

### Numbers

| Type | Size    | Endianness | Signed   | Minimum              | Maximum             |
|------|---------|------------|----------|----------------------|---------------------|
| byte | 8 bits  | -          | Unsigned | 0                    | 255                 |
| int  | 32 bits | Big        | Signed   | -2147483648          | 2147483647          |
| long | 64 bits | Big        | Signed   | -9223372036854775808 | 9223372036854775807 |

### Type[]

| Type | Size    | What                         |
|------|---------|------------------------------|
| int  | 4 bytes | Array length                 |
| T    | -       | Nth item, array length times |

### String

* byte[]
* UTF-8

## Mesage

| Value    | What                                   | Parameters             |                      |
|----------|----------------------------------------|------------------------|----------------------|
| `byte` 0 | Channel data                           | `byte` channelId       | `byte[]` channelData |
| `byte` 1 | Connection request / accept            | `byte` protocolVersion | `string` name        |
| `byte` 2 | Reject connection request / disconnect | `byte` statusCode      |                      |
| `byte` 3 | Ping                                   | `long` time            |                      |
| `byte` 4 | Answer ping                            | `long` originalTime    | `long` timeReceived  |

| Parameter       | Meaning                    |
|-----------------|----------------------------|
| channelId       | Channel ID                 |
| channelData     | Raw channel data           |
| protocolVersion | Protocol version           |
| name            | Server / client name       |
| statusCode      | Reject / disconnect reason |
| time            | Time sent                  |
| originalTime    | Original ping time sent    |
| timeReceived    | Time received              |
