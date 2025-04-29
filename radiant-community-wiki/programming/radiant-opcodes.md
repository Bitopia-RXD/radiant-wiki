# Radiant Opcodes

The Radiant blockchain introduced a set of opcodes that significantly improves on the capability of the Bitcoin technology it's based on. All these opcodes will be outlined in this article.

### Terms <a href="#terms" id="terms"></a>

* **Ref:** A 36 byte reference, either of normal or singleton type. A reference is created from an input's outpoint and can be propagated with every spend of a UTXO. For a ref to exist in an output there must be a matching input ref of the same type or an input with a matching outpoint. The ref type cannot be changed once it is created.
* **Normal ref**: A type of reference that can be propagated to one or more outputs.
* **Singleton ref:** A type of reference that can only ever exist in a single UTXO. Cannot be propagated to multiple outputs.
* **State script:** The part of the script before and not including an `OP_STATESEPARATOR`. Useful for storing state data that can be changed by the contract.
* **Code script:** The part of the script from and including an `OP_STATESEPARATOR`. If no state separator is present, the code script is the entire script.
* **`codeScriptHash`:** The double SHA-256 of the code script.

### Hash functions <a href="#hash-functions" id="hash-functions"></a>

SHA-512/256 is the hash function used by Radiant's proof of work algorithm. It is available in script as single and double hash functions. These can be used to validate Radiant block headers in script.

| Word             | Hex | Input | Output | Description        |
| ---------------- | --- | ----- | ------ | ------------------ |
| OP\_SHA512\_256  | ce  | bytes | hash   | SHA-512/256        |
| OP\_HASH512\_256 | cf  | bytes | hash   | Double SHA-512/256 |

### Induction opcodes <a href="#induction-opcodes" id="induction-opcodes"></a>

| Word                            | Hex | Input       | Output  | Description                                                                                                                                                                           |
| ------------------------------- | --- | ----------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OP\_PUSHINPUTREF                | d0  | ref         | ref     | Propagates a ref to an output. A ref of normal type must exist in an input or an input must have an outpoint matching the ref. Ref will be left on the stack.                         |
| OP\_PUSHINPUTREFSINGLETON       | d8  | ref         | ref     | Propagates a singleton ref to an output. A ref of singleton type must exist in an input or an input must have an outpoint matching the ref. Ref will be left on the stack.            |
| OP\_REQUIREINPUTREF             | d1  | ref         | ref     | A ref of normal type must exist in an input. Ref is not propagated. Ref will be left on the stack.                                                                                    |
| OP\_DISALLOWPUSHINPUTREF        | d2  | ref         | ref     | Requires a ref to not exist in any input. Leaves the ref on the stack.                                                                                                                |
| OP\_DISALLOWPUSHINPUTREFSIBLING | d3  | ref         | ref     | Requires a ref to not exist in any input sibling. Leaves the ref on the stack.                                                                                                        |
| OP\_REFTYPE\_UTXO               | d9  | ref         | type    | Get the type of a ref from transaction inputs. Returns 0 (not found), 1 (normal type) or 2 (singleton type).                                                                          |
| OP\_REFTYPE\_OUTPUT             | da  | ref         | type    | Get the type of a ref from transaction outputs. Returns 0 (not found), 1 (normal type) or 2 (singleton type).                                                                         |
| OP\_REFHASHDATASUMMARY\_UTXO    | d4  | inputIndex  | summary | For the input of the given index returns a hash256 of `<nValue><hash256(scriptPubKey)><numRefs><hash(sortedMap(pushRefs))>`                                                           |
| OP\_REFHASHDATASUMMARY\_OUTPUT  | d6  | outputIndex | summary | For the output of the given index returns a hash256 of `<nValue><hash256(scriptPubKey)><numRefs><hash(sortedMap(pushRefs))>`                                                          |
| OP\_REFDATASUMMARY\_UTXO        | e1  | inputIndex  | summary | Return refs used within an input. Pushes a vector of the form `<ref1><ref2><ref3>...`. If an input UTXO does not contain at least one reference, then the 36 byte zeroes are pushed.  |
| OP\_REFDATASUMMARY\_OUTPUT      | e2  | outputIndex | summary | Return refs used within an output. Pushes a vector of the form `<ref1><ref2><ref3>...`. If an input UTXO does not contain at least one reference, then the 36 byte zeroes are pushed. |

### State/code script opcodes <a href="#statecode-script-opcodes" id="statecode-script-opcodes"></a>

| Word                            | Hex | Input       | Output         | Description                                                                                                                                                              |
| ------------------------------- | --- | ----------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| OP\_STATESEPARATOR              | bd  |             |                | Separates the state script from the code script. Only one can exist in a script and it must not exist within an OP\_IF. No OP\_RETURN can exist in the script when used. |
| OP\_STATESEPARATORINDEX\_UTXO   | be  | inputIndex  | separatorIndex | Returns the byte index of the state separator for an input. Returns zero if no separator exists.                                                                         |
| OP\_STATESEPARATORINDEX\_OUTPUT | bf  | outputIndex | separatorIndex | Returns the byte index of the state separator for an output. Returns zero if no separator exists.                                                                        |
| OP\_CODESCRIPTBYTECODE\_UTXO    | e9  | inputIndex  | bytecode       | Returns the code script bytecode for an input.                                                                                                                           |
| OP\_CODESCRIPTBYTECODE\_OUTPUT  | ea  | outputIndex | bytecode       | Returns the code script bytecode for an output.                                                                                                                          |
| OP\_STATESCRIPTBYTECODE\_UTXO   | eb  | inputIndex  | bytecode       | Returns the state script bytecode for an output. Does not include the OP\_STATESEPARATOR.                                                                                |
| OP\_STATESCRIPTBYTECODE\_OUTPUT | ec  | outputIndex | bytecode       | Returns the state script bytecode for an output. Does not include the OP\_STATESEPARATOR.                                                                                |

### Count and sum opcodes <a href="#count-and-sum-opcodes" id="count-and-sum-opcodes"></a>

These opcodes provide a set queries on inputs and outputs by ref, ref hash and code script hash. Counts and sums can be performed over many outputs with a single opcode, meaning an unrolled loop in the script is not required.

| Word                                             | Hex | Input          | Output  | Description                                                                                                |
| ------------------------------------------------ | --- | -------------- | ------- | ---------------------------------------------------------------------------------------------------------- |
| OP\_REFHASHVALUESUM\_UTXOS                       | d5  | refHash        | photons | Returns the total sum of photons for inputs that match a 32 byte hash of the sorted set of ref asset ids.  |
| OP\_REFHASHVALUESUM\_OUTPUTS                     | d7  | refHash        | photons | Returns the total sum of photons for outputs that match a 32 byte hash of the sorted set of ref asset ids. |
| OP\_REFVALUESUM\_UTXOS                           | db  | ref            | photons | Returns the total sum of photons for inputs that contain a ref.                                            |
| OP\_REFVALUESUM\_OUTPUTS                         | dc  | ref            | photons | Returns the total sum of photons for outputs that contain a ref.                                           |
| OP\_REFOUTPUTCOUNT\_UTXOS                        | dd  | ref            | count   | Returns the count of inputs that contain a ref.                                                            |
| OP\_REFOUTPUTCOUNT\_OUTPUTS                      | de  | ref            | count   | Returns the count of outputs that contain a ref.                                                           |
| OP\_REFOUTPUTCOUNTZEROVALUED\_UTXOS              | df  | ref            | count   | Returns the count of inputs that contain a ref and contain zero photons.                                   |
| OP\_REFOUTPUTCOUNTZEROVALUED\_OUTPUTS            | e0  | ref            | count   | Returns the count of inputs that contain a ref and contain zero photons.                                   |
| OP\_CODESCRIPTHASHVALUESUM\_UTXOS                | e3  | codeScriptHash | photons | Returns the total sum of photons for inputs that have a `codeScriptHash`.                                  |
| OP\_CODESCRIPTHASHVALUESUM\_OUTPUTS              | e4  | codeScriptHash | photons | Returns the total sum of photons for outputs that have a `codeScriptHash`.                                 |
| OP\_CODESCRIPTHASHOUTPUTCOUNT\_UTXOS             | e5  | codeScriptHash | count   | Returns the count of inputs that have a `codeScriptHash`.                                                  |
| OP\_CODESCRIPTHASHOUTPUTCOUNT\_OUTPUTS           | e6  | codeScriptHash | count   | Returns the count of outputs that have a `codeScriptHash`.                                                 |
| OP\_CODESCRIPTHASHZEROVALUEDOUTPUTCOUNT\_UTXOS   | e7  | codeScriptHash | count   | Returns the count of inputs that have a `codeScriptHash` and contain zero photons.                         |
| OP\_CODESCRIPTHASHZEROVALUEDOUTPUTCOUNT\_OUTPUTS | e8  | codeScriptHash | count   | Returns the count of outputs that have a `codeScriptHash` and contain zero photons.                        |
