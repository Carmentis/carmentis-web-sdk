# Carmentis Client SDK

- [Methods](#methods)
- [Objects](#objects)

<a name="methods"></a>

# Methods

- [Blockchain methods](#blockchain_methods)
  - [getStatus()](#getStatus)
  - [getMasterBlockList()](#getMasterBlockList)
  - [getMasterBlock()](#getMasterBlock)
  - [getMicroChain()](#getMicroChain)
  - [getMicroBlock()](#getMicroBlock)
- [Key management methods](#key_management_methods)
  - [generateWordList()](#generateWordList)
  - [getMatchingWords()](#getMatchingWords)
  - [getSeedFromWordList()](#getSeedFromWordList)
  - [getWordListFromSeed()](#getWordListFromSeed)
  - [deriveKeyIdFromSeed()](#deriveKeyIdFromSeed)
  - [deriveKeyFromPassword()](#deriveKeyFromPassword)

<a name="blockchain_methods"></a>

## Blockchain methods

<a name="getStatus"></a>

### getStatus()

```js
async getStatus()
```

This method takes no argument.

**Returned value**

The following object is returned:

    {
      success: Boolean,
      data: chainStatusObject
    }

See [chainStatusObject](#chainStatusObject).

<a name="getMasterBlockList"></a>

### getMasterBlockList()

```js
async getMasterBlockList(firstBlockId, count)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `firstBlockId` | `Uint8Array` | yes | ID of the most recent master block
| `count` | `integer` | yes | Number of master blocks to retrieve

**Returned value**

The following object is returned:

    {
      success: Boolean,
      data: masterBlockListObject
    }

See [masterBlockListObject](#masterBlockListObject).

<a name="getMasterBlock"></a>

### getMasterBlock()

```js
async getMasterBlock(id)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `id` | `Uint8Array` | yes | ID of the master block

**Returned value**

The following object is returned:

    {
      success: Boolean,
      data: masterBlockObject
    }

See [masterBlockObject](#masterBlockObject).

<a name="getMicroChain"></a>

### getMicroChain()

```js
async getMicroChain(id)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `id` | `Uint8Array` | yes | ID of the microchain

**Returned value**

The following object is returned:

    {
      success: Boolean,
      data: microChainObject
    }

See [microChainObject](#microChainObject).

<a name="getMicroBlock"></a>

### getMicroBlock()

```js
async getMicroBlock(id)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `id` | `Uint8Array` | yes | ID of the microblock

**Returned value**

The following object is returned:

    {
      success: Boolean,
      data: microBlockObject
    }

See [microBlockObject](#microBlockObject).

<a name="key_management_methods"></a>

## Key management methods

<a name="generateWordList"></a>

### generateWordList()

```js
async generateWordList(nWords)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `nWords` | `integer` | no | The number of words to generate in [12 .. 24]. If not specified, the default is 12.

**Returned value**

An array of strings.

<a name="getMatchingWords"></a>

### getMatchingWords()

```js
async getMatchingWords(prefix)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `prefix` | `string` | yes | The prefix to search for.

**Returned value**

The dictionary words matching the prefix, as an array of strings.

<a name="getSeedFromWordList"></a>

### getSeedFromWordList()

```js
async getSeedFromWordList(words)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `words` | `string[]` | yes | An array of strings, typically obtained with `generateWordList()`.

**Returned value**

A seed, as an `Uint8Array`.

<a name="getSeedFromWordList"></a>

### getWordListFromSeed()

```js
async getWordListFromSeed(seed)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `seed` | `Uint8Array` | yes | The seed, e.g. obtained with `getSeedFromWordList()`.

**Returned value**

The list of words, as an array of strings.

<a name="deriveKeyIdFromSeed"></a>

### deriveKeyIdFromSeed()

```js
async deriveKeyIdFromSeed(seed)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `seed` | `Uint8Array` | yes | The seed, e.g. obtained with `getSeedFromWordList()`.

**Returned value**

A pair `[ masterKey, chainLinkId ]`, where both values are `Uint8Array`.

<a name="deriveKeyFromPassword"></a>

### deriveKeyFromPassword()

```js
async deriveKeyFromPassword(password)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `password` | `string` | yes | The password used for key derivation.

**Returned value**

An object with two methods: `encrypt` and `decrypt`.

**encrypt()**

```js
async encrypt(data, iv)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `data` | `Uint8Array` | yes | The data to be encrypted.
| `iv` | `Uint8Array` | no | An optional initialization vector that defaults to all 0's. As long as the key is used to encrypt a single kind of data (typically a master key), this argument can be safely ignored.

**Returned value**

An `Uint8Array`.

**decrypt()**

```js
async decrypt(data, iv)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `data` | `Uint8Array` | yes | The encrypted data.
| `iv` | `Uint8array` | no | The initialization vector used with the `encrypt()` method (defaults to all 0's).

**Returned value**

An `Uint8Array`, or `false` if the decryption failed.

<a name="objects"></a>

# Objects

- [chainStatusObject](#chainStatusObject)
- [masterBlockListObject](#masterBlockListObject)
- [masterBlockObject](#masterBlockObject)
- [microChainObject](#microChainObject)
- [microBlockObject](#microBlockObject)

