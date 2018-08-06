# Abstract

So, there is a proposal to implement addressing registry as a 
```
map<Name, Row[Record, Record, ...]>
``` 
with several constraints on it:


# `Name` description
`Name` - UTF-8 string with variadic length (1..N). 
(Ideally, there should not be any constraints on name's length, but it can be limited by the ethereum itself. Expertise iis needed).

#### Q: Why UTF-8 coding is neccesary?
A: 1. UTF-8 is standard encoding for Linux/modern Windows/modern MAC (with some nuances).
2. FDNS is also oriented on IoT devices, so the human-readability is not high-priority requirement, but the record compactness is.

###
`Name`s contraints:
1. `Name` - MUST be unique in map's keys space.
1. `Name` MUST reject any values that contains dots ("." would be used as a separator for names chaines) 


# `Row`s description:
`Row` should be implemented as `lis`t of `Record`s with variadic length and ability to append/remove items.

### `Row`s constraints:
1. `Row` MUST contains at least one `Record`.
1. `Row` MUST NOT contains 2 or more equal `Record`s.


# `Record` description:
```c++
class Record {    // Base type of records.
    byte type;    // (enum). Please, see `Records types enum` section for the details.
    byte[] body;  // Variadic bytes length array. (Up to eth block size (?)).
}
```

## Records types enum
Type | Predestination
--- | ---
0 | FDNS Record - Anchor to another FDNS record.
1 | IPv4 Record - 4 bytes long IPv4 address.
2 | IPv6 Record - 16 bytes long record IPv6 address.
3 | Classic DNS Record.
... | ...
64 | First availabe user-space record type.

* Records types up to 63 are protocol reserved.
* Records types between 64 and 255 are frre to use for custom users needs.

## Proposed records types
```c++
class FDNSRecord(Record){
  static byte type = 0;
  static byte[] body = {};  // UTF-8 string that is present in FDNS map. 
                            // Format {bytes4 - size, rest - string content}
}  
```

```c++
class IPv4Record(Record){
  static byte type = 1;
  static byte[4] body;      // BigEndian formatted IPv4 in bytes representation.
}  
```

```c++
class IPv6Record(Record){
  static byte type = 2;
  static byte[16] body;     // BigEndian formatted IPv6 in bytes representation.
}  
```

```c++
class DNSRecord(Record){
  static byte type = 3;
  static byte[] body = {};  // UTF-8 string that represents DNS-record.
}  
```

### `Record` constraints
1. `Record.body` can't be zero-length.

# Records ownership
1. Each one pair <`Name`, `Record`> MUST belong to ethereum address (ethereum account).
1. Contract MUST check if record with received `Name` is already present. In case if it is present - only it's owner MUST be able to update it.
