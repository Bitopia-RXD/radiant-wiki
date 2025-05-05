# Language - Global Functions & Operators

CashScript has several functions builtin for things like cryptographic and arithmetic applications. It also includes many common operators, although some important ones are notably missing due to the limitations of the underlying Bitcoin Script.

## Arithmetic functions <a href="#arithmetic-functions" id="arithmetic-functions"></a>

### abs() <a href="#abs" id="abs"></a>

```solidity
int abs(int a)
```

Returns the absolute value of argument `a`.

### min() <a href="#min" id="min"></a>

```solidity
int min(int a, int b)
```

Returns the minimum value of arguments `a` and `b`.

### max() <a href="#max" id="max"></a>

```solidity
int max(int a, int b)
```

Returns the maximum value of arguments `a` and `b`.

### within() <a href="#within" id="within"></a>

```solidity
bool within(int x, int lower, int upper)
```

Returns `true` if and only if `x >= lower && x < upper`.

## Hashing functions <a href="#hashing-functions" id="hashing-functions"></a>

### ripemd160() <a href="#ripemd160" id="ripemd160"></a>

```solidity
bytes20 ripemd160(any x)
```

Returns the RIPEMD-160 hash of argument `x`.

### sha1() <a href="#sha1" id="sha1"></a>

```solidity
bytes20 sha1(any x)
```

Returns the SHA-1 hash of argument `x`.

### sha256() <a href="#sha256" id="sha256"></a>

```solidity
bytes32 sha256(any x)
```

Returns the SHA-256 hash of argument `x`.

### hash160() <a href="#hash160" id="hash160"></a>

```solidity
bytes20 hash160(any x)
```

Returns the RIPEMD-160 hash of the SHA-256 hash of argument `x`.

### hash256() <a href="#hash256" id="hash256"></a>

```solidity
bytes32 hash256(any x)
```

Returns the double SHA-256 hash of argument `x`.

## Signature checking functions <a href="#signature-checking-functions" id="signature-checking-functions"></a>

{% hint style="info" %}
**Caution:** All signature checking functions must comply with the [NULLFAIL](https://github.com/bitcoin/bips/blob/master/bip-0146.mediawiki) rule. This means that if you want to use the output of a signature check inside the condition of an if-statement, the input signature needs to either be correct, or an empty byte array. When you use an incorrect signature as an input, the script will fail.
{% endhint %}

### checkSig() <a href="#checksig" id="checksig"></a>

```solidity
bool checksig(sig s, pubkey pk)
```

Checks that transaction signature `s` is valid for the current transaction and matches with public key `pk`.

### checkMultiSig() <a href="#checkmultisig" id="checkmultisig"></a>

```solidity
bool checkMultiSig(sig[] sigs, pubkey[] pks)
```

Performs a multi-signature check using a list of transaction signatures and public keys.

:::note While this function can be used inside your smart contracts, it is not supported by the JavaScript SDK, so it is recommended not to use it. Instead a `checkMultiSig()` call can be simulated using multiple `checkSig()` calls. :::

### checkDataSig() <a href="#checkdatasig" id="checkdatasig"></a>

```solidity
bool checkDataSig(datasig s, bytes msg, pubkey pk)
```

Checks that sig `s` is a valid signature for message `msg` and matches with public key `pk`.

## Operators <a href="#operators" id="operators"></a>

An overview of all supported operators and their precedence is included below. Notable is a lack of exponentiation, since these operations are not supported by the underlying Bitcoin Script.

| Precedence | Description                         | Operator                 |
| ---------- | ----------------------------------- | ------------------------ |
| 1          | Parentheses                         | `(<expression>)`         |
| 2          | Type cast                           | `<type>(<expression>)`   |
| 3          | Object instantiation                | `new <class>(<args...>)` |
| 4          | Function call                       | `<function>(<args...>)`  |
| 5          | Tuple index                         | `<tuple>[<index>]`       |
| 6          | Member access                       | `<object>.<member>`      |
| 7          | Unary minus                         | `-`                      |
| 7          | Logical NOT                         | `!`                      |
| 8          | Multiplication, division and modulo | `*`, `/`, `%`            |
| 9          | Addition and subtraction            | `+`, `-`                 |
| 9          | String / bytes concatenation        | `+`                      |
| 10         | Numeric comparison                  | `<`, `>`, `<=`, `>=`     |
| 11         | Equality and inequality             | `==`, `!=`               |
| 12         | Bitwise AND                         | `&`                      |
| 13         | Bitwise XOR                         | `^`                      |
| 14         | Bitwise OR                          | \|                       |
| 15         | Logical AND                         | `&&`                     |
| 16         | Logical OR                          | \|\|                     |
| 17         | Assignment                          | `=`                      |
