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
        - a double precision is interpreted as a 64 bit unsigned integer
        - b double precision is interpreted as a 64 bit unsigned integer
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
    
        得到两个双精度解的结果，解释为64位无符号整数该函数首先将两个输入重新解码为双精度（50位十进制数字精度），用分母分隔分子，然后将结果重新解释为64位无符号整数。 如果b为零（在reinterpret_cast加倍后）将引发错误.
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
    
        获取两个double之间的相等检查结果在进行相等检查之前，此函数将首先重新解释两个输入以重复（50位十进制数字精度）    
    - parameter
        - a 双精度解析为64位无符号整数
        - b 双精度解析为64位无符号整数
    - return
        - 如果第一个输入等于第二个输入，则为1，否则为0　　
        　
Example:

```c++
int64_t a = double_div( i64_to_double(10), i64_to_double(10) );
uint64_t b = double_div( i64_to_double(5), i64_to_double(2) );
uint64_t res = double_eq( a, b );
printi(res); // Output: 0
```
- <h5 id="double_gt">double_gt()</h5>
    > uint32_t double_gt(uint64_t a, uint64_t 	b )     
    
        两个双精度进行大于比较获得大的一个，此函数首先将两个输入重新解释为双精度（50个十进制数精度）。    
    - parameter
        - a 双精度解析为64位无符号整数
        - b 双精度解析为64位无符号整数
    - return
        - 如果第一个输入大于于第二个输入，则为1，否则为0　　
        　
Example:

```c++
uint64_t a = double_div( i64_to_double(10), i64_to_double(10) );
uint64_t b = double_div( i64_to_double(5), i64_to_double(2) );
uint64_t res = double_gt( a, b );
printi(res); // Output: 0
```

- <h5 id="double_lt">double_lt()</h5>
    > uint32_t double_lt(uint64_t a, uint64_t 	b )     
    
        获得两个双精度小于比较的结果，该函数首先将两个输入重新解码为双精度（50个十进制数字精度）。    
    - parameter
        - a 双精度解析为64位无符号整数
        - b 双精度解析为64位无符号整数
    - return
        - 如果第一个输入小于于第二个输入，则为1，否则为0
        　　　　
Example:

```c++
uint64_t a = double_div( i64_to_double(10), i64_to_double(10) );
uint64_t b = double_div( i64_to_double(5), i64_to_double(2) );
uint64_t res = double_lt( a, b );
printi(res); // Output: 1
```

- <h5 id="double_mult">double_mult()</h5>
    > uint64_t double_mult(uint64_t a, uint64_t 	b )     
    
        获得两个double之间的乘法结果，解释为64位无符号整数此函数首先将两个输入重新解码为双精度（50位十进制精度），然后将它们相乘，然后reinterpret_cast将结果重新解析为64位无符号整数。   
    - parameter
        - a 双精度解析为64位无符号整数
        - b 双精度解析为64位无符号整数
    - return
        - 相乘的结果reinterpret_cast转换为64位无符号整数
        　　　
Example:

```c++
uint64_t a = double_div( i64_to_double(10), i64_to_double(10) );
uint64_t b = double_div( i64_to_double(5), i64_to_double(2) );
uint64_t res = double_mult( a, b );
printd(res); // Output: 2.5
```
- <h5 id="double_to_i64">double_to_i64()</h5>
    > uint64_t double_to_i64(uint64_t a )     
    
        将double（解释为64位无符号整数）转换为64位无符号整数。 该函数首先将输入重新解码为双精度（50位十进制数字精度），然后将其转换为双精度，然后将其重新解码为64位无符号整数。    
    - parameter
        - a 双精度解析为64位无符号整数
    - return
        -　64位无符号整数转换结果　
        　　
Example:

```c++
uint64_t a = double_div( i64_to_double(5), i64_to_double(2) );
uint64_t res = double_to_i64( a );
printi(res); // Output: 2
```

- <h5 id="i64_to_double">i64_to_double()</h5>
    > uint64_t i64_to_double(uint64_t a )     
    
        将double（解释为64位无符号整数）转换为64位无符号整数。 该函数首先将输入重新解码为双精度（50位十进制数字精度），然后将其转换为双精度，然后将其重新解码为64位无符号整数。    
    - parameter
        - a 双精度解析为64位无符号整数
    - return
        -　double类型转换结果　　　

Example:

```c++
uint64_t res = i64_to_double( 3 );
printd(res); // Output: 3
```
<h5 id="multeq_i128">multeq_i128()</h5>
  > uint64_t multeq_i128(uint128_t *  self, const uint128_t *   other )     
    
        将两个128位无符号整数相乘，并将该值赋给第一个参数。
  - parameter
    - self 指向要相乘的值的指针。它将被替换为结果
    - other 指向要相乘的值的指针。
  - return
    -　double类型转换结果　　　

Example:

```c++
uint128_t self(100);
uint128_t other(100);
multeq_i128(&self, &other);
printi128(self); // Output: 10000

```


## Math CPP API   

    定义常用的数学函数和帮助器类型.

<h5>Fixed Point</h5>

    定点变量的32,64,128,256位版本

<h5>Real number</h5>

    带有基本操作符的实数数据类型。 封装double类Math C API.

<h2>类</h2>
<h5>struct  	eosio::uint128</h5>
        
    封装了uint128整数并定义常见运算符重载的结构。

<h2>函数</h2>

##### void [eosio::multeq](#multeq) (uint128_t& self, const uint128_t& other)
 	封装了multeq_i128　Math C API。

##### void [eosio::diveq](#diveq) (uint128_t& self, const uint128_t& other)
 	封装了diveq_i128 Math C API。

<h5>template<typename T ></h5>
T 	[eosio::min](#min) (const T& a, const T& b)
 	
 	定义了类似std::min()函数。

<h5>template<typename T ></h5>
T 	[eosio::max](#max) (const T& a, const T& b)
 	
 	定义了类似std::max()函数。

<h2>函数文档</h2>

<h5 id="diveq">diveq()</h5>
  > void eosio::diveq	(uint128_t& self,const uint128_t& other) | inline      

    将两个128位无符号整数相除，并将该值赋给第一个参数。 如果other值为零，它将抛出异常。 封装了Math C API的diveq_i128      
  - Parameters
       - self	分子. 它的值将被结果替代。
       - other	分母。
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
        
        获取最大值。
  - parameter
      - a　比较值
      - b　比较值
  - return
    获取a和b中更大的一个. 如果相等返回a
Example:
```
uint128_t a(1);
uint128_t b(2);
std::cout << max(a, b); // Output: 2
```

<h5 id="min">min()</h5>
   > template<typename T >   
   > T eosio::min(const T& a, const T& b)		

    获取更小的一个值
   - parameter
     - a 比较值
     - b 比较值
   - return
        获取a和b中更小的一个. 如果相等返回a
Example:
```
uint128_t a(1);
uint128_t b(2);
std::cout << min(a, b); // Output: 1
```

<h5 id="multeq">multeq()</h5>
   > void eosio::multeq	(uint128_t& self, const uint128_t& other )	 <span class="mlabel">inline</span>

    将两个128位无符号整数相乘，并将该值赋给第一个参数。 这是对multeq_i128 Math C API的封装.
   - parameter
      - self	相乘的值. 它的值将被结果替代。
      - other	相乘的值.
Example:
```
uint128_t self(100);
uint128_t other(100);
multeq(self, other);
std::cout << self; // Output: 10000
```
