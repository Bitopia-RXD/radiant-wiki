# Language - Types

CashScript is a statically typed language, which means that the type of each variable needs to be specified. Types can also be implicitly or explicitly cast to other types. For a quick reference of the various casting possibilities, see [Type Casting](language-types.md#type-casting).

## Boolean <a href="#boolean" id="boolean"></a>

`bool`: The possible values are constants `true` and `false`.

Operators:

* `!` (logical negation)
* `&&` (logical conjunction, “and”)
* `||` (logical disjunction, “or”)
* `==` (equality)
* `!=` (inequality)

{% hint style="info" %}
**Note:** The operators `||` and `&&` don't apply common short-circuiting rules. This means that in the expression `f(x) || g(y)`, `g(y)` will still be executed even if `f(x)` evaluates to true.
{% endhint %}

## Integer <a href="#integer" id="integer"></a>

`int`: Signed integer of 64 bit size.

Operators:

* Comparisons: `<=`, `<`, `==`, `!=`, `>=`, `>` (all evaluate to `bool`)
* Arithmetic operators: `+`, `-`, unary `-`, `*`, `/`, `%` (modulo).

Note the clear lack of the `**` (exponentiation) operator as well as any bitwise operators.

{% hint style="info" %}
**Caution:** The script will fail when the right hand side of Division and modulo operations is zero.
{% endhint %}

### Date Parsing <a href="#date-parsing" id="date-parsing"></a>

Dates and times are always represented as integers. To get the UTC timestamp of a date use the built-in parser to avoid any potential errors. This will take a date in the format `date("YYYY-MM-DDThh:mm:ss")` and convert it to an integer timestamp.

#### **Example**

```solidity
int timestamp = date("2021-02-17T01:30:00");
require(timestamp == 1613554200);
```

## String <a href="#string" id="string"></a>

`string`: UTF8-encoded byte sequence.

Operators:

* `+` (concatenation)
* `==` (equality)
* `!=` (inequality)

Members:

* `length`: Number of characters in the string.
* `split(int)`: Splits the string at the specified index and returns a tuple with the two resulting strings.
* `reverse()`: Reverses the string.

{% hint style="info" %}
**Caution:** The script will fail if `split()` is called with an index that is out of bounds.&#x20;
{% endhint %}

## Bytes <a href="#bytes" id="bytes"></a>

`bytes`: Byte sequence. Can optionally be bound to a byte length by specifying e.g. `bytes4`, `bytes32`, `bytes64`. It is also possible to use `byte` as an alias for `bytes1`.

Operators:

* `+` (concatenation)
* `==` (equality)
* `!=` (inequality)

Members:

* `length`: Number of bytes in the sequence.
* `split(int)`: Splits the byte sequence at the specified index and returns a tuple with the two resulting byte sequences.
* `reverse()`: Reverses the byte sequence.

{% hint style="info" %}
**Caution:** The script will fail if `split()` is called with an index that is out of bounds.&#x20;
{% endhint %}

## Bytes types with semantic meaning <a href="#bytes-types-with-semantic-meaning" id="bytes-types-with-semantic-meaning"></a>

Some byte sequences hold specific meanings inside Bitcoin Cash contracts. These have been granted their own types separate from the regular `bytes` type.

### Public Key <a href="#public-key" id="public-key"></a>

`pubkey`: Byte sequence representing a public key. Generally 33 bytes long.

Operators:

* `==` (equality)
* `!=` (inequality)

### Transaction Signature <a href="#transaction-signature" id="transaction-signature"></a>

`sig`: Byte sequence representing a transaction signature. Generally 65 bytes long.

Operators:

* `==` (equality)
* `!=` (inequality)

### Data Signature <a href="#data-signature" id="data-signature"></a>

`datasig`: Byte sequence representing a data signature. Generally 64 bytes long.

Operators:

* `==` (equality)
* `!=` (inequality)

## Array <a href="#array" id="array"></a>

Arrays are not assignable and can only be used with the `checkMultisig` function using the following syntax:

```solidity
checkMultisig([sig1, sig2], [pk1, pk2, pk3]);
```

## Tuple <a href="#tuple" id="tuple"></a>

Tuples are the type that is returned when calling the `split` member function on a `string` or `bytes` type. Their first or second element can be accessed through an indexing syntax similar to other languages:

```solidity
string question = "What is Bitcoin Cash?";
string answer = question.split(15)[0].split(8)[1];
```

It is also possible to assign both sides of the tuple at once with a destructuring syntax:

```solidity
string bitcoin, string cash = "BitcoinCash".split(7);
require(bitcoin == cash);
```

## Type Casting <a href="#type-casting" id="type-casting"></a>

Type casting can be done both explicitly and implicitly as illustrated below. `pubkey`, `sig` and `datasig` can be implicitly cast to `bytes`, meaning they can be used anywhere where you would normally use a `bytes` type. Explicit type casting can be done with a broader range of types, but is still limited. The syntax of this explicit type casting is illustrated below. Note that you can also cast to bounded `bytes` types.

{% hint style="info" %}
**Note:** When casting integer types to bytes of a certain size, the integer value is padded with zeros. e.g. `bytes4(0) == 0x00000000`. It is also possible to pad with a variable number of zeros, by passing in a `size` parameter, which indicates the size of the output. e.g. `bytes(0, 4 - 2) == 0x0000`.
{% endhint %}

{% hint style="info" %}
**Caution:** When casting bytes types to integer, you should be sure that the bytes value fits inside a 64-bit signed integer, or the script will fail.
{% endhint %}

See the following table for information on which types can be cast to other which other types.

| Type    | Implicitly castable to | Explicitly castable to |
| ------- | ---------------------- | ---------------------- |
| int     |                        | bytes, bool            |
| bool    |                        | int                    |
| string  |                        | bytes                  |
| bytes   |                        | sig, pubkey, int       |
| pubkey  | bytes                  | bytes                  |
| sig     | bytes                  | bytes                  |
| datasig | bytes                  | bytes                  |

#### **Example**

```solidity
pubkey pk = pubkey(0x0000);
bytes editedPk = bytes(pk) + 0x1234;
bytes4 integer = bytes4(25);
```
