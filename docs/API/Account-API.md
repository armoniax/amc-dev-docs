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
    * balance - a pointer to a series of memory that stores   
    * len - > * * length of memory for storing balance data       
> * Return:     
    * If the account is retrieved as returned: `true`   
> * Premise:   
    * Data is a valid pointer to a memory range at least datalen bytes long      
    * Data is the pointer to the balance object\*((uint64_t\*)data)to store the primary key   
    
Example:
```C
balance b;
b.account = N(myaccount);
balance(b, sizeof(balance));
```

# Account CPP API    
C++ API for querying account data. Example: account balance

## Class
> struct  [eosio::account::account_balance](#h2_tag)　　  
Binary structure of account balance

## Function
* bool eosio::accout::get(account_balance &acnt)  
Return an account balance structure

## 函数说明
* <h5>bool eosio::account::get(account_balance & acnt) </h5>  
 	返回一个账户余额结构

>* 参数:
    * acnt - 账户
>* 返回  
如果找到帐户的余额，则为`true`

<h2><span id="h2_tag">eosio::account::account_balance 类型说明</span></h2>
账户余额的二进制结构


\#include<account.hpp\>


### 公共属性

* <h5>account_name 	[account](#account)   </h5>
 	所查余额的账户名称
 
* <h5>asset [eos_balance](#eos_balance)  </h5>
 	账户的余额
 
* <h5>asset 	[staked_balance](#staked_balance)  </h5> 
 	账户的抵押余额
 
* <h5>asset 	[unstaking_balance](#unstaking_balance)   </h5>
 	账户正在取消抵押的余额
 
* <h5>time 	[last_unstaking_time](#last_unstaking_time) </h5>  
 	这个账户最后取消抵押余额的时间</h5>

### 详细的描述
例子:
```c++
account_balance test1_balance;
test1_balance.account = N(test1);
if (account_api::get(test1_balance))
{
   eosio::print("test1 balance=", test1_balance.eos_balance, "\n");
}
```

### 数据成员说明文档

<h5 id="account">account</h5>
> account_name eosio::account::account_balance::account   

        所查余额的账户名称

<h5 id="eos_balance">eos_balance</h5>
> asset eosio::account::account_balance::eos_balance   
        
     账户的余额

<h5 id="last_unstaking_time">last_unstaking_time</h5>   
>time eosio::account::account_balance::last_unstaking_time   

    账户正在取消抵押的余额

<h5 id="staked_balance">staked_balance</h5>
> asset eosio::account::account_balance::staked_balance   

    账户的抵押余额

<h5 id="unstaking_balance">unstaking_balance</h5>
> asset eosio::account::account_balance::unstaking_balance   

    这个账户最后取消抵押余额的时间

### 源文档
<h5> contracts/eosiolib/account.hpp</h5>
