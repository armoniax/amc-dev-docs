# Database API

Store and retrieve the data of Armonia blockchain. It organizes data according to the following structure.

# Module

## Database C API    
C API of database.

### Description

- code - the name of the account with write permission.
- scope - the account where the data is stored.
- table - name of the table being stored.
- record - a row in the table.

Each transaction specifies a set of valid ranges that can be read and / or written. The running code determines what can be written. Therefore, the write operation does not allow you to specify / configure the code.

>  Attention

>  Attempting to read and / or write outside the valid range and / or part of the code will cause your transaction to fail.

### Table type

Supported table type determined by its number and size：
1. dbi64

databasecpp provides a simple API for storing fixed size structure as database rows.
