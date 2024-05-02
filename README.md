# Methods

- [Blockchain methods](#blockchain)
- [Key management methods](#keys)

<a name="blockchain"></a>

## Blockchain methods

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
      data: masterblockListObject
    }

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
      data: microchainObject
    }

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
      data: microblockObject
    }

<a name="keys"></a>

## Key management methods

### generateWordList()

```js
async generateWordList(nWords)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `id` | `integer` | no | The number of words to generate in [12 .. 24]. If not specified, the default is 12.

**Returned value**
An array of strings.

### getMatchingWords()

```js
async getMatchingWords(prefix)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `prefix` | `string` | yes | The prefix to search for.

**Returned value**
The dictionary words matching the prefix, as an array of strings.

### deriveFromWordList()

```js
async deriveFromWordList(words)
```

| Argument | Type | Mandatory | Description |
| - |:-:|:-:| - |
| `words` | `string[]` | yes | An array of strings, typically obtained with `generateWordList()`.

**Returned value**
A pair `[ publicId, masterKey ]`, where both `publicId` and `masterKey` are `Uint8Array`.

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
| `iv` | `Uint8array` | no | The nonce used with the `encrypt()` method (defaults to all 0's).

**Returned value**
An `Uint8Array`, or `false` if the decryption failed.
