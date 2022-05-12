# Modules


Here is a list of all the modules:

- [Smart contract API reference](Smart Contract.md)  

  - [AMAX-RPC](API/AMAX-RPC.md) - Describe how to use HTTP RPC of amnod.

  - [Account API](API/Account-API.md) - query account data.

    - [Account C API](API/Account-API.md#Account C API) - C API for querying account data.
    - [Account C++ API](API/Account-API.md#Account C++ API) - C++ API for querying account data. 

  - [Action API](API/Action-API.md) - define the API used to query action attributes.

    - [Action C API](API/Action-API.md#Action C API) - define the API used to query operation attributes.
    - [Action C++ API](API/Action-API.md#Action C++ API) - safe C++ encapsulation of Action C API.

  - [Builtin Types](API/Builtin Types.md) - define typedefs and alias.

  - [Chain API](API/Chain-API.md) - query the internal state of the chain.

    - [Chain C API](API/Chain-API.md#Chain C API) - query the internal state of the chain.

  - [Console API](API/Console-API.md) - enable applications to log / print messages.

    - [Console C API](API/Console-API.md#Console C API) - C API that enables applications to record / print text messages.
    - [Console C++ API](API/Console-API.md#Console C++ API) - C++ encapsulation of Console C API.

  - [Database API](API/Database-API.md) - Store and retrieve the data of Armonia blockchain. It organizes data according to the following structure.

    - [Database C API](API/Database-API.md#Database C API) - C API of database.

  - [Math API](API/Math-API.md) - define common mathematical functions.

    - [Math C API](API/Math-API.md#Math C API) - define basic mathematical operations that use more complicated abstraction.
    - [Math C++ API](API/Math-API.md#Math C++ API) - define common math functions and helper types.
      - [Fixed Point](API/Math-API.md#Fixed Point) - define the 32, 64, 128, 256 bit version of the variable.
      - [Real number](API/Math-API.md#Real number) - a real number data type with basic operators. 

  - [System API](API/System-API.md) - define the API used to interact with system level internal functions.

    - [Privileged API](API/System-API.md#Privileged API) - define the API for accessing configuration links, which can only be used by privileged accounts.
    - [Privileged C API](API/System-API.md#Privileged C API) - define privileged C API.
    - [System C API](API/System-API.md#System C API) - define the API for interacting with system-level internal functions.

  - [Token API](API/Token-API.md) - define the API used to interact with standard compliant token messages and database tables.

  - [Transaction API](API/Transaction-API.md) - define the API used to send transactions and inline messages

    - [Transaction C API](API/Transaction-API.md#Transaction C API) - define the API used to send transactions
    - [Transaction C++ API](API/Transaction-API.md#Transaction C++ API) - safe C++ encapsulation of Transaction C API

