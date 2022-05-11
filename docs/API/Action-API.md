# Action API

Define the C API for querying operation properties.

# Module


## Action C API   
Defines the API for querying operation properties.

### Function

##### uint32_t [read_action_data](#read_action_data) (void *msg, uint32_t len)

 	Copy the current operation data to the specified location.
 
##### uint32_t [action_data_size](#action_data_size) ()

 	Get the size of the current operation's data field.
 
##### void [require_recipient](#require_recipient) (account_name name)
 	
 	Add the specified account to the set of accounts to be notified.
 
##### void [require_auth](#require_auth) (account_name name)

 	Verify that the specified account exists in the set of authorizations provided.
 
##### bool [has_auth](#has_auth) (account_name name)
 
##### void [require_auth2](#require_auth2) (account_name name, permission_name permission)
 	
 	Verify that the specified account exists in the set of authorizations provided.
 
##### void [send_inline](#send_inline) (char *serialized_action, size_t size)
 
##### void [send_context_free_inline](#send_context_free_inline) (char *serialized_action, size_t size)
 
##### void [require_write_lock](#require_write_lock) (account_name name)
 	
 	Verify that the name exists in the set of write locks held.
 
##### void [require_read_lock](#require_read_lock) (account_name name)

 	Verify that the name exists in the set of write locks held.
 
##### time [publication_time](#publication_time) ()

 	Get the publication time.
 
##### account_name [current_sender](#current_sender) ()

 	Get the current sender of the operation.
 
##### account_name [current_receiver](#current_receiver) ()

 	Get the current receiver of the operation.
 	
### Description

AMAX's action has the following abstract structure：    

```c++
struct action {
  scope_name scope; // the contract defining the primary code to execute for code/type
  action_name name; // the action to be taken
  permission_level[] authorization; // the accounts and permission levels provided
  bytes data; // opaque data processed by code
};
```
    This API enables your contract to check the fields of the current operation and take action accordingly.

Example：

```c++
// Assume this action is used for the following examples:
// {
//  "code": "eos",
//  "type": "transfer",
//  "authorization": [{ "account": "inita", "permission": "active" }],
//  "data": {
//    "from": "inita",
//    "to": "initb",
//    "amount": 1000
//  }
// }
char buffer[128];
uint32_t total = read_action(buffer, 5); // buffer contains the content of the action up to 5 bytes
print(total); // Output: 5
uint32_t msgsize = action_size();
print(msgsize); // Output: size of the above action's data field
require_recipient(N(initc)); // initc account will be notified for this action
require_auth(N(inita)); // Do nothing since inita exists in the auth list
require_auth(N(initb)); // Throws an exception
print(now()); // Output: timestamp of last accepted block
```

### Function docs

<h5 id="action_data_size">action_data_size()</h5>
   > uint32_t action_data_size()

    Getting the length of the data field of the current action is very useful for dynamically sized action.

   - return    
    The size of the data field of the current operation.
    
<h5 id="current_receiver">current_receiver()</h5>
   > account_name current_receiver()	

   Get the receiver of the action.

   - return
     Account of the receiver of the current action
     
<h5 id="current_sender">current_sender()</h5>
   > account_name current_sender()

    Get the sender of the action.

   - return
     Account of the sender of the current action

<h5 id="has_auth">has_auth()</h5>
   > bool has_auth(account_name name)
   
<h5 id="publication_time">publication_time()</h5>
   > time publication_time()

    return publication_time time in seconds in 1970.

   - return       
    return publication_time time in seconds in 1970.
    
<h5 id="read_action_data">read_action_data()</h5>
   > uint32_t read_action_data(void * msg, uint32_t len)		

    Copy the len bytes of the current operation data to the specified location

   - parameter    
        - msg	- A pointer that can copy up to len bytes of the current operation data
        - len	- len current operation data to be copied  
   - return    
        Number of bytes copied to MSG

        
<h5 id="require_auth">require_auth()</h5>
   > void require_auth(account_name name)

    Verify that the name exists in the authentication set provided in the operation. If not found, throws.

   - parameter    
        name　- name of the account to be verified
        
<h5 id="require_auth2">require_auth2()</h5>
   >void require_auth2(account_name name,permission_name permission)		

    Verify that the name exists in the authentication set provided in the operation. If not found, throws.

  - parameter    
    - name	- name of the account to be verified    
    - permission	- verify the permission level    

<h5 id="require_read_lock">require_read_lock()</h5>
   > void require_read_lock(account_name name)	

    Verify that the name of the read lock saved in the action exists. If not found, throws.

   - parameter    
      - name	- name of the account to be verified    
<h5 id="require_recipient">require_recipient()</h5>
   > void require_recipient(account_name name)	

    Add the specified account to the set of accounts to be notified

   - parameter    
        - name	- name of the account to be verified   
        
<h5 id="require_write_lock">require_write_lock()</h5>
   > void require_write_lock(account_name name)	

    Verify that the name exists in the set of write locks saved in the operation. If not found, throws.

   - parameter    
       - name	- name of the account to be verified
       
<h5 id="send_context_free_inline">send_context_free_inline()</h5>
   > void send_context_free_inline(char * serialized_action, size_t size)		

    Send free inline in the context of the parent transaction of this operation

   - parameter    
        - serialized_action	- serialization operation    
        - size	- the size of the serialization operation, in bytes

<h5 id="send_inline">send_inline()</h5>
   >void send_inline(char * serialized_action, size_t size)

    Send free inline in the context of the parent transaction of this operation

   - parameter    
        - serialized_action	- serialization operation    
        - size	- The size of the serialization operation, in bytes   

## Action CPP API   
Type safe C++ encapsulation of Action C API


### Class
##### struct  [eosio::permission_level]()
 
##### struct  [eosio::action]()
 
##### struct  [eosio::action_meta< Account, Name >]()
 
### Function

###### template< typename T \>
> T 	eosio::[current_action_data](#current_action_data) ()
 	
 	Explain the action subject as type T.
 
###### template< typename T \>
T 	eosio::[unpack_action_data](#unpack_action_data) ()
 
###### template< typename... accounts \>

void eosio::[require_recipient](#require_recipient) (account_name name, accounts... remaining_accounts)
 	
 	Verify that the specified account exists in a set of notification accounts.
 
void 	eosio::[require_auth](#require_auth) (const permission_level &level)
 
###### template< typename T , typename... Args \>

void 	eosio::[dispatch_inline](#dispatch_inline) (permission_level perm, account_name code, action_name act, void(T::*)(Args...), std::tuple< Args... > args)
 

### Description
---
> Note：
> Action C API中有一些方法可以直接从C++中使用.

### Function docs

<h5 id="current_action_data">current_action_data()</h5>
> template< typename T \>    
> T eosio::current_action_data()	

    此方法尝试将操作主体重新解释为T类型。这仅在操作没有动态字段且T类型的结构包装已正确定义时才起作用。

Example:
```
struct dummy_action {
  char a; //1
  unsigned long long b; //8
  int  c; //4
};
dummy_action msg = current_action_data<dummy_action>();
```

<h5 id="dispatch_inline">dispatch_inline()</h5>
> template< typename T,typename... Args \>   
> void eosio::dispatch_inline(permission_level perm,account_name code, action_name act, void(T::*)(Args...) ,std::tuple<Args... >args )		

<h5 id="require_auth">require_auth()</h5>
> void eosio::require_auth(const permission_level& level)	

<h5 id="require_recipient">require_recipient()</h5>
> template<typename... accounts \>    
> void eosio::require_recipient(account_name name, accounts... remaining_accounts)
		
    所有列出的账户将被添加到要通知的账户集合中

    这种辅助方法使您能够通过一次调用将多个账户添加到要通知列表的账户，而不必多次调用类似的C API。

> Note:
> action.code也被视为通知帐户集的一部分

Example:
```
require_recipient(N(Account1), N(Account2), N(Account3)); // throws exception if any of them not in set.
```

<h5 id="unpack_action_data">unpack_action_data()</h5>
> template<typename T \>
> T eosio::unpack_action_data()
