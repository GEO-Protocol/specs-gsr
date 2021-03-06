

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
Each message must pe prefixed by size header and protocol version:  
`4B Message Size`, `1B Protocol Ver = 0`, `[NB] Payload`. 

**Note:**  
Field `Message Size` must not include itself.  
For example if payload size == 10, then `Message Size` must be equal 10.

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
 1B Request Type = 128
24B TxID, 
 2B Members Count  

{ Member 1
      2B Tx Member ID
    16Kb Member PubKey 
}
{ Member 2 }
...
{ Member N }
```
`CONNECTION DROP ON OBS. SIDE`

------
<br/>

### Request: Claim Is Present
```
 1B Request Type = 130
24B TxID
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
 1B Request Type = 64
24B TxID, 
 2B Members Count  

{ Member 1
     2B Tx Member ID
    8Kb Member Signature 
}
{ Member 2 }
...
{ Member N }
```
`CONNECTION DROP ON OBS. SIDE`

------
<br/>

### Request: TSL Is Present
```
 1B Request Type = 66
24B TxID
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
24B TxID
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
    { Member 2 }
    ...
    { Member N }
}
```
`CONNECTION DROP ON OBS. SIDE`

-------
<br/>

### Request: TransactionsStates
```
1B Request Type = 192
2B Transactions IDs count
{ 24B TxID1
   8B Final Block Number
   16B TxUUID
}
{ 24B TxID2 }
  ...
{ 24B TxIDn }
```

### Response: TransactionsStates
```
2B States count
{ State 1 
  1B State: 
  0 - No info;
  1 - Claim in pool;
  2 - Claim in chain;
  3 - TSL in chain;
}
{ State 2 }
...
{ State n }
```
`CONNECTION DROP ON OBS. SIDE`
