

## Interface

| Parameter     | Value         |
| ------------- | ------------- |
| Protocol      | TCP (binary)  |
| Default Port  | 4000          |

<br/>

## Description
Current implementation of the GEO Node communication protocol is **syncronous**:  
client must wait for (and then read) the response right after the request was sent.
After response sending observer would close the connection, 
because it is assumed that GEO Node would perform no more than one request for some period of time.
In case if request does not assumes any reponse - connection would be closed immedeatly after request accepting.

The motivation to close connections ASAP is to keep observer capable to process requests from as many GEO Nodes, as possible.
Current architecture of the `Observer <-> GEO Node` communication assumes as less data transfers as possible. 

<br/>

## Messages Structure
Each message must pe prefixed by size header: `4B Message Size` `[NB] Payload`  
Max. message size = `32 Mb` = `33554432 B`  
Min. message size = `1B`

<br/>

### Request: Last Block Number
`1B Request Type = 32`

### Response: Last Block Number
`1B Request Type = 32`  
`CONNECTION DROP ON OBS. SIDE`

------
<br/>

### Request: Claim Append
```
1B  Request Type = 128
16B TxID, 
2B  Members Count  

{ Member 1
    2B   Tx Member ID
    16Kb Member PubKey 
}
{ Member ... }
{ Member N }
```
`CONNECTION DROP ON OBS. SIDE`

------
<br/>

### Request: Claim Is Present
```
1B Request Type = 130
16B TxID
```

### Response: Claim Is Present
```
1B Present In Pool [true/false]
8B Block number in which Claim is present, or 0 if no such block.
```

------
<br/>

### Request: TSL Append
```
1B  Request Type = 64
16B TxID, 
2B  Members Count  

{ Member 1
    2B   Tx Member ID
    8Kb Member Signature 
}
{ Member ... }
{ Member N }
```
`CONNECTION DROP ON OBS. SIDE`

------
<br/>

### Request: TSL Is Present
```
1B Request Type = 66
16B TxID
```

### Response: TSL Is Present
```
1B Present In Pool [true/false]
8B Block number in which TSL is present, or 0 if no such block.
```
`CONNECTION DROP ON OBS. SIDE`

------
<br/>

### Request: TSL GET
```
1B Request Type = 68
16B TxID
```

### Response: TSL Get
```
1B Is present [True/False]
{ TSL, only present if "IsPresent" = True 
    2B  Members Count
    { Member 1
        2B  Tx Member ID
        8Kb Member Signature 
    }
    { Member ... }
    { Member N }
}
```
`CONNECTION DROP ON OBS. SIDE`
