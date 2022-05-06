Builtin Types
---

Define typedefs and alias.

Module
---

> [fixed size key sorted lexicographically(sorted in dictionary order)]()  

> [Variable Length Integer(variable Length Integer)]()

Class
---

> struct [public key]()   

> struct [signature]()

> struct [checksum256]()

> struct [checksum160]()

> struct [checksum512]()

> struct [fixed_string16]()

> struct [fixed_string32]()

> struct [account_permission]()

> struct [eosio::name]()   
> Encapsulate a [uint64_t]() to ensure that it is only passed to the expected Name.


Macro
---

> \#define [PACKED(X)](#PACKED) __attribute((packed)) X

> \#define [N(X)](#N) ::eosio::string_to_name(#X)   
> Used to generate a compilation time from the base32 string interpretation of X [uint64_t]()

Type definition
---


> typedef [uint64_t]() 	[account_name](#permission_name)

> typedef [uint64_t]() 	[permission_name](#permission_name)

> typedef [uint64_t]() 	[token_name](#token_name)

> typedef [uint64_t]() 	[table_name](#table_name)

> typedef [uint32_t]() 	[time](#time)

> typedef [uint64_t]() 	[scope_name](#scope_name)

> typedef [uint64_t]() 	[action_name](#action_name)

> typedef [uint16_t]() 	[region_id](#region_id)

> typedef [uint64_t]() 	[asset_symbol](#asset_symbol)

> typedef [int64_t]() 	[share_type](#share_type)

> typedef [uint16_t]() 	[weight_type](#weight_type)

> typedef struct [checksum256]() 	[transaction_id_type](#transaction_id_type)

> typedef struct [fixed_string16]() 	[field_name](#field_name)

> typedef struct [fixed_string32]() 	[type_name](#type_name)




