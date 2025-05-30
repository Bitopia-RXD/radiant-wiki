# scryptlib

Javascript/TypeScript SDK for integration of Radiant (~~RAD~~ RXD) Blockchain Smart Contracts written in the sCrypt language.

PLEASE NOTE: ~~This is a fork of scryptlib as a convenience that contains the patches to the included bsv.js lib directly~~ **Alternatively, the regular scryptlib may be used along with&#x20;**~~**radjs**~~**&#x20;radiantjs** ~~https://github.com/RadiantBlockchain/radjs~~ [https://github.com/chainbow/radiantjs](https://github.com/chainbow/radiantjs) (latest) or [https://github.com/RadiantBlockchain-Community/radiantjs](https://github.com/RadiantBlockchain-Community/radiantjs) and not using the bundled bsv in scryptlib.

[![Build Status](https://travis-ci.com/sCrypt-Inc/scryptlib.svg?branch=master)](https://travis-ci.com/sCrypt-Inc/scryptlib)

[https://github.com/sCrypt-Inc/scryptlib](https://github.com/sCrypt-Inc/scryptlib)

You can install `scryptlib` in your project as below:

```
$ npm install scryptlib
```

A smart contract is compiled to a locking script template. A contract function call is transformed to an unlocking script. Developers are responsible for setting the locking and unlocking scripts of a transaction properly before sending it to the Bitcoin network. This may include some actions described below:

* Instantiate locking script: replace the constructor formal parameters, represented by placeholders in the locking script template, with actual parameters/arguments to form the complete locking script.
* Assemble unlocking script: convert the arguments of a contract function call to script format and concatenate them to form the unlocking script.

By using `scryptlib`, both scripts can be obtained with ease.

### Contract Description File <a href="#contract-description-file" id="contract-description-file"></a>

The compiler output results in a JSON file. It’s a representation used to build locking and unlocking scripts. We call this file a **contract description file**.

{% file src="../../.gitbook/assets/counter_debug_desc.json" %}

There are three ways to generate this file (named as `xxx_desc.json`):

1. Use [**sCrypt VS Code extension**](https://marketplace.visualstudio.com/items?itemName=bsv-scrypt.sCrypt) to compile manually;
2. Use the function `compile` programmatically:

```javascript
  import { compile } from 'scryptlib';

  ...

  compile(
    {
      path: contractFilePath  //  the file path of the contract
    },
    {
      desc: true  // set this flag to be `true` to get the description file output
      asm: true // set this flag to be `true` to get the asm file output
      optimize: false //set this flag to be `true` to get optimized asm opcode
      sourceMap: true //set this flag to be `true` to get source map
      hex: true //set this flag to be `true` to get hex format script
      stdout: false//set this flag to be `true` to make that the compiler will output the compilation result through stdout
    }
  );
```

1. `compileAsync` is the asynchronous version of the function `compile`

```javascript
  import { compileAsync } from 'scryptlib';

  ...

  compileAsync(
    {
      path: contractFilePath  //  the file path of the contract
    },
    settings
  ) : Promise<CompileResult>;
```

1. Run `npx` command in CLI:

```sh
  # install compiler binary
  npx scryptlib download
  # compiling contract
  npx scryptlib your_directory/your_scrypt.scrypt
```

### Types <a href="#types" id="types"></a>

#### 1. Basic Types <a href="#id-1-basic-types" id="id-1-basic-types"></a>

All basic types of the **sCrypt** language have their corresponding javascript classes in scryptlib. In this way, the type of parameters could be checked and potential bugs can be detected before running.

|   Types (scrypt)  |           scryptlib (javascript/typescript)           |
| :---------------: | :---------------------------------------------------: |
|       `int`       |          `new Int(1)` or `number` or `bigint`         |
|       `bool`      |             `new Bool(true)` or `boolean`             |
|      `bytes`      | `new Bytes('0001')` or `new String("hello world 😊")` |
|      `PubKey`     |                  `new PubKey('0001')`                 |
|     `PrivKey`     |                    `new PrivKey(1)`                   |
|       `Sig`       |                   `new Sig('0001')`                   |
|    `Ripemd160`    |                `new Ripemd160('0001')`                |
|       `Sha1`      |                   `new Sha1('0001')`                  |
|      `Sha256`     |                  `new Sha256('0001')`                 |
|   `SigHashType`   |                `new SigHashType('01')`                |
| `SigHashPreimage` |            `new SigHashPreimage('010001')`            |
|    `OpCodeType`   |                 `new OpCodeType('76')`                |

#### 2. Array Types <a href="#id-2-array-types" id="id-2-array-types"></a>

scryptlib uses javascript array to represent the array types of the **sCrypt** language.

```typescript

[[1, 3, 1]] // represent `int[1][3]` in **sCrypt** language

[new Bytes("00"), new Bytes("00"), new Bytes("00")] // represent `bytes[3]` in **sCrypt** language

```

#### 3. Structure and Type Aliases <a href="#id-3-structure-and-type-aliases" id="id-3-structure-and-type-aliases"></a>

Composite types, including structs and type aliases, are dynamically generated by `buildTypeClasses`. When creating a structure, all members must specify values. Use dot to access structure members.

Structure and type aliases defined in sCrypt:

```javascript
struct Person {
    bytes addr;
    bool isMale;
    int age;
}

struct Block {
    bytes hash;
    bytes header;
    int time;
}

type Male = Person;
type Female = Person;

contract Main {
    Person person;
    int x;

    ...

}

```

Access Structure and type aliases by **SDK** :

```typescript

const PersonContract = buildContractClass(loadDescription('person_desc.json'));

/*Person is structure and Male, Female are type aliases */
const { Person, Male, Female } = buildTypeClasses(PersonContract);

let man = new Person({
    isMale: true,
    age: 14,
    addr: new Bytes("68656c6c6f20776f726c6421")
  });

man.age = 20;

let woman = new Female({
    isMale: false,
    age: 18,
    addr: new Bytes("68656c6c6f20776f726c6421")
  });

woman.addr = new Bytes("")

```

#### 4. Library <a href="#id-4-library" id="id-4-library"></a>

Library is another composite types. When the constructor parameter of the contract contains library, we need to create library through sdk.

Library defined in sCrypt:

```javascript
library L {
  private int x;

  constructor(int a, int b) {
    this.x = a + b;
  }
  function f() : int {
    return this.x;
  }
}

contract Test {
  public int x;
  L l;

  public function unlock(int x) {
    require(this.l.f() == x + this.x);
  }
}
```

Access Library by **SDK** :

```typescript

const Test = buildContractClass(loadDescription('test_desc.json'));

const { L } = buildTypeClasses(Test);

let test = new Test(1, new L(1, 2));

```

As you can see, creating a library instance is similar to creating a contract instance. Sometimes the constructor parameters of the library may be generic types. At this time, the sdk will deduce the generic type based on the constructor arguments you pass.

### Deploy a Contract and Call Its Function <a href="#deploy-a-contract-and-call-its-function" id="deploy-a-contract-and-call-its-function"></a>

Both **deploying a contract** and **calling a contract function** are achieved by sending a transaction. Generally speaking,

* deploying a contract needs the locking script in the output of this transaction to be set properly;
* calling a contract function needs the unlocking script in the input of this transaction to be set properly.

There are 2 steps.

#### 1. Get Locking and Unlocking Script <a href="#id-1-get-locking-and-unlocking-script" id="id-1-get-locking-and-unlocking-script"></a>

You can use the description file to build a reflected contract class in Javascript/TypeScript like this:

```typescript
const MyContract = buildContractClass(JSON.parse(descFileContent));
```

To create an instance of the contract class, for example:

```typescript
const instance = new MyContract(1234, true, ...parameters);
```

To get the locking script, use:

```typescript
const lockingScript = instance.lockingScript;
// To convert it to ASM/hex format
const lockingScriptASM = lockingScript.toASM();
const lockingScriptHex = lockingScript.toHex();
```

To get the unlocking script, just call the function and turn the result to `bsv.Script` object, for example:

```typescript
const funcCall = instance.someFunc(new Sig('0123456'), new Bytes('aa11ff'), ...parameters);
const unlockingScript = funcCall.toScript();
// To convert it to ASM/hex format
const unlockingScriptASM = unlockingScript.toASM();
const unlockingScriptHex = unlockingScript.toHex();
```

#### 2. Wrap Locking and Unlocking Script into a Transaction <a href="#id-2-wrap-locking-and-unlocking-script-into-a-transaction" id="id-2-wrap-locking-and-unlocking-script-into-a-transaction"></a>

[Chained APIs](chained-apis/) make building transactions super easy.

### Local Unit Tests <a href="#local-unit-tests" id="local-unit-tests"></a>

A useful method `verify(txContext)` is provided for each contract function call. It would execute the function call with the given context locally. The `txContext` argument provides some context information of the current transaction, **needed only if signature is checked inside the contract**.

```typescript
{
  tx?: any;                 // current transaction represented in bsv.Transaction object
  inputIndex?: number;      // input index, default value: 0
  inputSatoshis?: number;   // input amount in satoshis
}
```

It returns an object:

```typescript
{
  success: boolean;       // script evaluates to true or false
  error: string;          // error message, empty if success
}
```

It usually appears in unit tests, like:

```typescript
const context = { tx, inputIndex, inputSatoshis };

// 1) set context per verify()
const funcCall = instance.someFunc(new Sig('0123456'), new Bytes('aa11ff'), ...parameters);
const result = funcCall.verify(context);
// 2) alternatively, context can be set at instance level and all following verify() will use it
instance.txContext = context;
const result = funcCall.verify();

expect(result.success, result.error).to.be.true;
assert.isFalse(result.success, result.error);
```

### Contracts with State <a href="#contracts-with-state" id="contracts-with-state"></a>

sCrypt offers [stateful contracts](https://scryptdoc.readthedocs.io/en/latest/state.html#stateful-contract). Declare any property that is part of the state with a decorator `@state` in a contract, for example:

```typescript
contract Counter {
    @state
    int counter;

    constructor(int counter) {
        this.counter = counter;
    }
}
```

Use the initial state to instantiate the contract and read the state by accessing the properties of the contract instance.

```typescript
const instance = new Counter(0);

let state = instance.counter;
// update state
instance.counter++;
```

Then use `instance.getNewStateScript()` to get a locking script that includes the new state. It accepts an object as a parameter. Each key of the object is the name of a state property, and each value is the value of the state property. You should provide all state properties in the object.

```typescript
const tx = newTx(inputSatoshis);
let newLockingScript = instance.getNewStateScript({
    counter: 1
});

tx.addOutput(new bsv.Transaction.Output({
  script: newLockingScript,
  satoshis: outputAmount
}))

preimage = getPreimage(tx, instance.lockingScript, inputSatoshis)

```

You can also access the state of the contract by accessing the properties of the instance.

```typescript

instance.counter++;
instance.person.name = new Bytes('0001');

```

You can also maintain state manually to, for example, optimize your contract or use customized state de/serialization [rawstate](https://radiant4people.com/programming/rad-scryptlib/docs/rawstate/).

### Instantiate Inline Assembly Variables <a href="#instantiate-inline-assembly-variables" id="instantiate-inline-assembly-variables"></a>

Assembly variables can be replaced with literal Script in ASM format using `replace()`. Each variable is prefixed by its unique scope, namely, the contract and the function it is under.

```typescript
const asmVars = {
  'contract1.function1.variable1': 'ff41',
  'contract2.function2.variable2': 'OP_4'
};
instance.replaceAsmVars(asmVars);
```

You could find more examples using `scryptlib` in the [boilerplate](https://github.com/sCrypt-Inc/boilerplate) repository.

### Construct contracts from raw transactions <a href="#construct-contracts-from-raw-transactions" id="construct-contracts-from-raw-transactions"></a>

In addition to using a constructor to create a contract, you can also use a raw transaction to construct it.

```typescript
const axios = require('axios');

const Counter = buildContractClass(loadDesc("counter_debug_desc.json"));
let response = await axios.get("https://api.whatsonchain.com/v1/bsv/test/tx/7b9bc5c67c91a3caa4b3212d3a631a4b61e5c660f0369615e6e3a969f6bef4de/hex")
// constructor from raw Transaction.
let counter = Counter.fromTransaction(response.data, 0/** output index**/);

// constructor from Utxo lockingScript
let counterClone = Counter.fromHex(counter.lockingScript.toHex());

```

### Support browsers that are not compatible with BigInt <a href="#support-browsers-that-are-not-compatible-with-bigint" id="support-browsers-that-are-not-compatible-with-bigint"></a>

Some contracts use `Bigint` to construct or unlock. but some browsers do not support `Bigint`, such as IE11. In this case, we use strings to build `Bigint`.

```typescript

// polyfill

import 'react-app-polyfill/ie11';  
import 'core-js/features/number';
import 'core-js/features/string';
import 'core-js/features/array';



let demo = new Demo("11111111111111111111111111111111111", 1);

let result = demo.add(new Int("11111111111111111111111111111111112")).verify();

console.assert(result.success, result.error)
```
