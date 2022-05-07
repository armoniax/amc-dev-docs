# Chain API

Query the internal status of chain.

## Chain C API

### Function

- uint32_t 	[get_active_producers](#get_active_producers) (account_name *producers, uint32_t datalen)


### Description 

### Function description

- <h5> <span id="get_active_producers">get_active_producers()</span></h5>
    > uint32_t get_active_producers	(account_name * producers, uint32_t 	datalen)
    - returns a collection of active producers
    - parameter
        - producers - a point to account_name's buffer
        - datalen - byte length of the buffer
    - return
        - number of bytes actually filled
     
    
- example
```
account_name producers[21];
uint32_t bytes_populated = get_active_producers(producers, sizeof(account_name)*21);
```
