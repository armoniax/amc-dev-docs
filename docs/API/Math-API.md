# Math API

Define common mathematical functions.

# Module

## Math C API   
Define basic mathematical operations that use higher abstraction.

### Function

- <h5> void 	[multeq_i128](#multeq_i128) (uint128_t *self, const uint128_t *other)</h5>
 	- Multiply by two 128 bit unsigned bit integers. If the pointer is invalid, an exception is thrown.

- <h5> void 	[diveq_i128](#diveq_i128) (uint128_t *self, const uint128_t *other)</h5>
 	- Divides two 128 bit unsigned bit integers and throws an exception when the pointer is invalid.

- <h5> uint64_t 	[double_add](#double_add) (uint64_t a, uint64_t b)</h5>
 	- Add between double types.

- <h5> uint64_t 	[double_mult](#double_mult) (uint64_t a, uint64_t b)</h5>
 	- Multiply between double types.

- <h5>uint64_t 	[double_div](#double_div) (uint64_t a, uint64_t b)</h5>
 	- Divide between double types.

- <h5>uint32_t 	[double_lt](#double_lt) (uint64_t a, uint64_t b)</h5>
 	- Compare which double type is smaller.

- <h5>uint32_t 	[double_eq](#double_eq) (uint64_t a, uint64_t b)</h5>
 	- Double type equality comparison.

- <h5>uint32_t 	[double_gt](#double_gt) (uint64_t a, uint64_t b)</h5>
 	- Compare which double type is larger.

- <h5>uint64_t [double_to_i64](#double_to_i64) (uint64_t a)</h5>
 	- Convert a double to a 64 bit unsigned integer。

- <h5>uint64_t 	[i64_to_double](#i64_to_double) (uint64_t a)</h5>
 	- Converts a 64 bit unsigned integer to double (interpreted as a 64 bit unsigned integer).

### Description

### Function description

- <h5> <span id="diveq_i128">diveq_i128()</span></h5>

    > void diveq_i128	(uint128_t * self, const uint128_t *  other )   
    
        Divide two 128 bit unsigned integers and assign the value to the first parameter. If the other value is 0, it throws an exception.   
    - parameter
        - self a pointer to molecule. It will be replaced with the result.
        - other a pointer to denominator　　　


Example:
```c++
uint128_t self(100);
uint128_t other(100);
diveq_i128(&self, &other);
printi128(self); // Output: 1
```

- <h5 id="double_add">double_add()</h5>

    > uint64_t double_add( uint64_t a, uint64_t b)    
    
        The addition result between two double is obtained and parsed into 64 bit unsigned integer. This function first decodes the two inputs into double precision (50 decimal digit precision), adds them, and then reinterpret_ Cast re parses the result into a 64 bit unsigned integer.　　　
    - parameter
        - a double is interpreted as 64 bit unsigned integer
        - b double is interpreted as 64 bit unsigned integer
    - return
        - reinterpret_cast add the result of the 64 bit unsigned integer
        　　　　

Example:
```c++
uint64_t a = double_div( i64_to_double(5), i64_to_double(10) );
uint64_t b = double_div( i64_to_double(5), i64_to_double(2) );
uint64_t res = double_add( a, b );
printd(res); // Output: 3
```
- <h5 id="double_div">double_div()</h5>
    > uint64_t double_div(uint64_t a, uint64_t 	b )     
    
        The results of two double are obtained and interpreted as 64 bit unsigned integers. The function first redecodes the two inputs into double (50 bit decimal precision), separates the numerators with denominators, and then reinterprets the results as 64 bit unsigned integers. If b is zero (after reinterpret_cast is doubled), an error will appear.
    - parameter
        - a double molecules are interpreted as 64 bit unsigned integers
        - b double denominators are interpreted as 64 bit unsigned integers
    - return
        - result of division reinterpret_cast is converted to unsigned integer　
    
Example:
```c++
uint64_t a = double_div( i64_to_double(10), i64_to_double(100) );
printd(a); // Output: 0.1
```
- <h5 id="double_eq">double_eq()</h5>
    > uint32_t double_eq(uint64_t a, uint64_t 	b )     
    
        Gets the result of the equality check between two doubles. Before performing the equality check, this function first reinterprets the two inputs to repeat (50 decimal precision)
    - parameter
        - a double is interpreted as 64 bit unsigned integer
        - b double is interpreted as 64 bit unsigned integer
    - return
        - If the first input is equal to the second input, it's 1, otherwise it's 0.　
        　
         
Example:
```c++
int64_t a = double_div( i64_to_double(10), i64_to_double(10) );
uint64_t b = double_div( i64_to_double(5), i64_to_double(2) );
uint64_t res = double_eq( a, b );
printi(res); // Output: 0
```
- <h5 id="double_gt">double_gt()</h5>
    > uint32_t double_gt(uint64_t a, uint64_t 	b )     
    
        Two double are compared to obtain the larger one. This function first reinterprets the two inputs as double (50 decimal precision).    
    - parameter
        - a double is interpreted as 64 bit unsigned integer
        - b double is interpreted as 64 bit unsigned integer
    - return
        - If the first input is larger than the second input, it's 1, otherwise it's 0.　　
        　
         
Example:
```c++
uint64_t a = double_div( i64_to_double(10), i64_to_double(10) );
uint64_t b = double_div( i64_to_double(5), i64_to_double(2) );
uint64_t res = double_gt( a, b );
printi(res); // Output: 0
```

- <h5 id="double_lt">double_lt()</h5>
    > uint32_t double_lt(uint64_t a, uint64_t 	b )     
    
        Two double are compared to obtain the smaller one. This function first reinterprets the two inputs as double (50 decimal precision).    
    - parameter
        - a double is interpreted as 64 bit unsigned integer
        - b double is interpreted as 64 bit unsigned integer
    - return
        - If the first input is smaller than the second input, it's 1, otherwise it's 0.
        　　　　
            
Example:
```c++
uint64_t a = double_div( i64_to_double(10), i64_to_double(10) );
uint64_t b = double_div( i64_to_double(5), i64_to_double(2) );
uint64_t res = double_lt( a, b );
printi(res); // Output: 1
```

- <h5 id="double_mult">double_mult()</h5>
    > uint64_t double_mult(uint64_t a, uint64_t 	b )     
    
        Obtain the multiplication result between two doubles and interpret it as 64 bit unsigned integer. This function first decodes the two inputs into double (50 bit decimal precision), then multiplies them, and then reinterpret_ cast interprets the result into a 64 bit unsigned integer.   
    - parameter
        - a double is interpreted as 64 bit unsigned integer
        - b double is interpreted as 64 bit unsigned integer
    - return
        - reinterpret_cast interprets the result into a 64 bit unsigned integer
        　　　
           
Example:
```c++
uint64_t a = double_div( i64_to_double(10), i64_to_double(10) );
uint64_t b = double_div( i64_to_double(5), i64_to_double(2) );
uint64_t res = double_mult( a, b );
printd(res); // Output: 2.5
```
- <h5 id="double_to_i64">double_to_i64()</h5>
    > uint64_t double_to_i64(uint64_t a )     
    
        Convert a double (interpreted as a 64 bit unsigned integer) to a 64 bit unsigned integer. This function first redecodes the input to double (50 bit decimal precision), then converts it to double, and then redecodes it to 64 bit unsigned integer.    
    - parameter
        - a double is interpreted as 64 bit unsigned integer
    - return
        - 64 bit unsigned integer　
        　　
          
Example:
```c++
uint64_t a = double_div( i64_to_double(5), i64_to_double(2) );
uint64_t res = double_to_i64( a );
printi(res); // Output: 2
```

- <h5 id="i64_to_double">i64_to_double()</h5>
    > uint64_t i64_to_double(uint64_t a )     
    
        Convert a double (interpreted as a 64 bit unsigned integer) to a 64 bit unsigned integer. This function first redecodes the input to double (50 bit decimal precision), then converts it to double, and then redecodes it to 64 bit unsigned integer.    
    - parameter
        - a double is interpreted as 64 bit unsigned integer
    - return
        -　double conversion result　　　


Example:
```c++
uint64_t res = i64_to_double( 3 );
printd(res); // Output: 3
```
<h5 id="multeq_i128">multeq_i128()</h5>
  > uint64_t multeq_i128(uint128_t *  self, const uint128_t *   other )     
    
        Multiplies two 128 bit unsigned integers and assigns the value to the first parameter.
        
  - parameter
    - self pointer to the value to be multiplied. It will be replaced with the result.
    - other pointer to the value to be multiplied
  - return
    -　double conversion result　　　

Example:
```c++
uint128_t self(100);
uint128_t other(100);
multeq_i128(&self, &other);
printi128(self); // Output: 10000

```


## Math CPP API   

    Define common functions and helper types.

<h5>Fixed Point</h5>

    32,64128256 bit version of fixed-point variables

<h5>Real number</h5>

    Real data type with basic operator. Encapsulate double class math C API

<h2>class</h2>
<h5>struct  	eosio::uint128</h5>
        
    Encapsulates the uint128 integer and defines the structure of common operator overloading.

<h2>function</h2>

##### void [eosio::multeq](#multeq) (uint128_t& self, const uint128_t& other)
 	Encapsulate multeq_i128　Math C API.

##### void [eosio::diveq](#diveq) (uint128_t& self, const uint128_t& other)
 	Encapsulate diveq_i128 Math C API.

<h5>template<typename T ></h5>
T 	[eosio::min](#min) (const T& a, const T& b)
 	
 	Define functions similar to std::min().

<h5>template<typename T ></h5>
T 	[eosio::max](#max) (const T& a, const T& b)
 	
 	Define functions similar to std::max().

<h2>Function docs</h2>

<h5 id="diveq">diveq()</h5>
  > void eosio::diveq	(uint128_t& self,const uint128_t& other) | inline      

    Divide two 128 bit unsigned integers and assign the value to the first parameter. If the other value is zero, it throws an exception. It encapsulates diveq_ i128 Math C API.  
 
  - Parameters
       - self	Molecule. Its value will be replaced by the result.
       - other	Denominator.
 
Example:
```
uint128_t self(100);
uint128_t other(100);
diveq(self, other);
std::cout << self; // Output: 1
```

<h5 id="max">max()</h5>
  > template<typename T \>    
  > T eosio::max(const T& a,const T& b )		
        
        Get the larger value.
 
  - parameter
      - a　comparison value
      - b　comparison value
  - return
    Get the larger of a and b. If equal, return a.
 
Example:
```
uint128_t a(1);
uint128_t b(2);
std::cout << max(a, b); // Output: 2
```

<h5 id="min">min()</h5>
   > template<typename T >   
   > T eosio::min(const T& a, const T& b)		

    Get the smaller value.
 
   - parameter
     - a comparison value
     - b comparison value
   - return
        Get the smaller of a and b. If equal, return a.
 
Example:
```
uint128_t a(1);
uint128_t b(2);
std::cout << min(a, b); // Output: 1
```

<h5 id="multeq">multeq()</h5>
   > void eosio::multeq	(uint128_t& self, const uint128_t& other )	 <span class="mlabel">inline</span>

    Multiply two 128 bit unsigned integers and assign the value to the first parameter. It encapsulates multeq_i128 Math C API.
 
   - parameter
      - self	The value of multiplication. Its value will be replaced by the result.
      - other	The value of multiplication.
 
Example:
```
uint128_t self(100);
uint128_t other(100);
multeq(self, other);
std::cout << self; // Output: 10000
```
