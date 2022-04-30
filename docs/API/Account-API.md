# Account API
# Account C API   
C API for querying account data.

## Function

> bool 	account_balance_get(void *balance, uint32_t len)   
retrieve the balance of the account provided

## Function docs

* <h5>account_balance_get()   </h5>
bool 	account_balance_get(void *balance, uint32_t len)   

> * Parameter:   
     * balance - a pointer to a series of memory that stores balance data  
     * len - length of memory for storing balance data      
> * Return:     
    If the account is retrieved as returned: `true`   
> * Premise:   
    Data is a valid pointer to a memory range at least datalen bytes long      
    Data is the pointer to the balance object\*((uint64_t\*)data) to store the primary key   
    
Example:
```C
balance b;
b.account = N(myaccount);
balance(b, sizeof(balance));
```

# Account CPP API    
C++ API for querying account data. Example: account balance.

## Class
> struct  [eosio::account::account_balance](#h2_tag)　　  
Binary structure of account balance

## Function
* bool eosio::accout::get(account_balance &acnt)  
Return an account balance structure

## Function description
* <h5>bool eosio::account::get(account_balance & acnt) </h5>  
 	return an account balance structure

>* Parameter:
    * acnt - account
>* Return  
If the account balance is found，it shows`true`

<h2><span id="h2_tag">eosio::account::account_balance type description</span></h2>
Binary structure of account balance

\#include<account.hpp\>


### Common property

* <h5>account_name 	[account](#account)   </h5>
 	account name of the balance checked
 
* <h5>asset [eos_balance](#eos_balance)  </h5>
 	account balance
 
* <h5>asset 	[staked_balance](#staked_balance)  </h5> 
 	staked balance of account
 
* <h5>asset 	[unstaking_balance](#unstaking_balance)   </h5>
 	unstaking balance of account
 
* <h5>time 	[last_unstaking_time](#last_unstaking_time) </h5>  
 	last unstaking time of account</h5>

### Description
Example:
```c++
account_balance test1_balance;
test1_balance.account = N(test1);
if (account_api::get(test1_balance))
{
   eosio::print("test1 balance=", test1_balance.eos_balance, "\n");
}
```

### Data description docs

<h5 id="account">account</h5>
> account_name eosio::account::account_balance::account   

     	account name of the balance checked

<h5 id="eos_balance">eos_balance</h5>
> asset eosio::account::account_balance::eos_balance   
        
     account balance

<h5 id="last_unstaking_time">last_unstaking_time</h5>   
>time eosio::account::account_balance::last_unstaking_time   

     unstaking balance of account

<h5 id="staked_balance">staked_balance</h5>
> asset eosio::account::account_balance::staked_balance   

    staked balance of account

<h5 id="unstaking_balance">unstaking_balance</h5>
> asset eosio::account::account_balance::unstaking_balance   

    last unstaking time of account

### Source docs
<h5> contracts/eosiolib/account.hpp</h5>
