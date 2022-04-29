# Modules


Here is a list of all the modules:

- [Armonia smart contract]() - interface for recording Armonia contracts.

- [.system Armonia System Contract]() - main component to define system contract

- [Smart contract API reference](Smart contract.md)  

  - [Account API](API/Account-API.md) - querying account data.

    - [Account C API](API/Account-API.md#Account C API) - querying C language of account data.
    - [Account CPP API](API/Account-API.md#Account CPP API) - C++ API for querying account data. Example: account balance

  - [Chain API](API/Chain-API.md) - querying the internal state of the chain.

    - [Chain C API](API/Chain-API.md#Chain C API) - querying the internal state of the chain.

  - [Database API](API/Database-API.md) - storing and retrieving The data API of IO blockchain organizes data according to the following broad structure.

    - [Database C API](API/Database-API.md#Database C API) - C API of database.

  - [Math API](API/Math-API.md) - defining common mathematical functions.

    - [Math C API](API/Math-API.md#Math C API) - defining basic mathematical operations that use more complicated abstraction.
    - [Math CPP API](API/Math-API.md#Math CPP API) - defining common math functions and helper types.
      - [Fixed Point](API/Math-API.md#Fixed Point) - defining the 32, 64, 128, 256 bit version of the variable.
      - [Real number](API/Math-API.md#Real number) - a real number data type with basic operators. 

  - [Action API](API/Action-API.md) - defining the API used to query action attributes.

    - [Action C API](API/Action-API.md#Action C API) - defining the API used to query operation attributes.
    - [Action CPP API](API/Action-API.md#Action CPP API) - safe C++ encapsulation of Action C API.

  - [Memory API]() - defining common memory functions.

    - [Memory C API]() - defining common memory functions.
    - [Memory C++ API]() - defining common memory functions.

  - [Console API](API/Console-API.md) - enabling applications to log / print messages.

    - [Console C API](API/Console-API.md#Console C API) - APIC API to enable applications to record / print messages.
    - [Console CPP API](API/Console-API.md#Console CPP API) - C++ encapsulation of Console C API.

  - [System API](API/System-API.md) - defining the API used to interact with system level internal functions.

    - [Privileged API](API/System-API.md#Privileged API) - defining the API for accessing configuration links, which can only be used by privileged accounts.
      - [Privileged C API](API/System-API.md#Privileged C API) - defining privileged C API.
    - [System C API](API/System-API.md#System C API) - defining the API for interacting with system-level internal functions.

  - [Token API](API/Token-API.md) - defining the API used to interact with standard compliant token messages and database tables.

  - [Transaction API](API/Transaction-API.md) - defining the API used to send transactions and messages

    - [Transaction C API](API/Transaction-API.md#Transaction C API) - defining the API used to send transactions
    - [Transaction CPP API](API/Transaction-API.md#Transaction CPP API) - safe C++ encapsulation of Transaction C API
    - [Builtin Types](API/Types.md) - specifying typedefs and aliases

    - [Variable Length Integer](API/Types.md#Variable Length Integer) 

  - [Example Storage]() - smart contract example

    - [Storage Contract]() - example of storing smart contract
    - [Tic Tac Toe Contract]() - example of defining PvP Tic Tac Toe contract
