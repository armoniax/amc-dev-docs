# Transaction API

Define the API for sending transactions and inline messages

## Transaction C API

Define the API used to send transactions

## Transaction C++ API  

Safe Transaction C++ encapsulation for C API 

### Description

AMAX transaction has the following abstract structure:

```C++
struct transaction {
  Name scope[]; 
  Name readScope[]; 
  message messages[]; 
};
```

This API enables your contract to build and send transactions.

Deferred transactions will not be processed until future blocks appear. Therefore, as long as they are well formed, they won't affect the success of their parent transaction. If any other condition causes the parent transaction to be marked as failed, the deferred transaction will never be processed.

Deferred transactions must comply with the permissions available to the parent transaction or can be delegated to the contract account for future use.

Inline message allows one contract to send a message to another contract. The message is processed immediately after the current message is processed, so that the success or failure of the parent transaction depends on the success of the message. If the inline message fails in processing, the entire transaction and message tree rooted in the block will be marked as failed, and any impact on the database will not last.

Because of this and the parallel nature of transactional applications, inline messages may not affect any scopes that are not listed in their parent transaction scopes. They may also not read their parent transaction scope or any scope not listed in readScope.

Inline messages and deferred transactions must comply with the permissions available to the parent transaction, or can be delegated to the contract account for future use.
