Smart Contract API
---             

Guidelines to write an Armonia smart contract.

Modules
----

> [Account API](API/Account-API.md)    
> querying account data.

> [Chain API](API/Chain-API.md)  
> querying the internal state of the chain.

> [Database API](API/Database-API.md)      
> storing and retrieving the data of Armonia blockchain and organizing data according to the structure.

> [Math API](API/Math-API.md)      
> defining common mathematical functions.

> [Action API](API/Action-API.md)      
> defining the API used to query action attributes.

> [Memory API](API/Memory-API.md)      
> defining common memory functions.

> [Console API](API/Console-API.md)      
> enabling applications to log / print messages.

> [System API](API/System-API.md)      
> defining the API used to interact with system level internal functions.

> [Token API](API/Token-API.md)      
> defining the API used to interact with standard compliant token messages and database tables.

> [Transaction API](API/Transaction-API.md)      
> defining the API used to send transactions and messages.

> [Builtin Types](API/Types.md)      
> specifying typedefs and aliases.


# Description

## Background

Armonia contracts (also known as applications) are deployed to the blockchain as precompiled Web Assemblies (also known as WASM). WASM is compiled from C / C++ using LLVM and clang. It means that you need the knowledge of C / C++ to develop your blockchain application. Although it can be developed in C, we strongly recommend that all developers use Armonia C++ API, which provides stronger security and is easier to read.

## Application structure

Armonia applications are designed around event (operation) handlers that respond to user actions. For example, a user may transfer a token to another user. The event can be handled and may be rejected by the sender, recipient, and the application itself. As an application developer, you can decide what operation users can take and which handlers they can or must call to respond to these events.

## API

Armonia has applications that are similar to traditional applications：

```C++
extern "C" {
   void init();
   void apply( uint64_t code, uint64_t action );
}
```

apply gives the parameter code and operation that uniquely identifies each event in the system. For example, code may be a currency contract and action may be a transfer. This event (code, action) may be passed to multiple contracts including senders and receivers. It's up to your application to decide how to respond to such events.
Init is another API called immediately after the code is loaded. This is where you should perform a state initialization.

## API application example

In general, you should use your application to dispatch events to a function that implements most of the logical functions, and the function can choose to reject events that the contract cannot or won't accept.

```c++
extern "C" {
   void apply( uint64_t code, uint64_t action ) {
      if( code == N(currency) ) {
         if( action == N(transfer) ) 
            currency::apply_currency_transfer( current_action< currency::transfer >() );
      } else {
         eosio_assert( false, "rejecting unexpected event" );
      }
   }
}
```

> Note   
> When defining API, you need to place them in the extern "C" code block so that C++ name modifications do not apply to the function.
