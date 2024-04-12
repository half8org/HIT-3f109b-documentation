---
description: If you are programming guru or just starting this might be of your interest.
---

# Programmatic or CLI

## Creating Wallets

How to create wallets using the CLI or programmatically

Although wallets are commonly created through the [MultiversX Web Wallet](https://wallet.multiversx.com/) or the [MultiversX Ledger App](https://docs.multiversx.com/wallet/ledger), one can also use the CLI or the SDK.

### **Generate a new mnemonic**[​](https://docs.multiversx.com/developers/creating-wallets/#generate-a-new-mnemonic) <a href="#generate-a-new-mnemonic" id="generate-a-new-mnemonic"></a>

Using [mxjs-wallet](https://www.npmjs.com/package/@multiversx/sdk-wallet-cli), a mnemonic phrase (24 words) can be generated as follows:

```
mxjs-wallet new-mnemonic --mnemonic-file=mnemonicOfAlice.txt
```

Programmatically using [sdk-wallet](https://www.npmjs.com/package/@multiversx/sdk-wallet), the same can be achieved through:

```
import { Mnemonic } from "@multiversx/sdk-wallet/mnemonic";

let mnemonic = Mnemonic.generate();
let words = mnemonic.getWords();
console.log(words);
```

### **Deriving a JSON key-file (from mnemonic)**[​](https://docs.multiversx.com/developers/creating-wallets/#deriving-a-json-key-file-from-mnemonic) <a href="#deriving-a-json-key-file-from-mnemonic" id="deriving-a-json-key-file-from-mnemonic"></a>

Using [mxjs-wallet](https://www.npmjs.com/package/@multiversx/sdk-wallet-cli), a JSON key-file can be obtained as follows:

```
mxjs-wallet derive-key --mnemonic-file=mnemonicOfAlice.txt \
 --account-index=0 \
 --key-file=keyOfAlice.json --password-file=passwordOfAlice.txt
```

Programmatically using [sdk-wallet](https://www.npmjs.com/package/@multiversx/sdk-wallet), the same can be achieved through:

```
const mnemonic = Mnemonic.generate();
const password = "insert a password here";
const addressIndex = 0;

const secretKey = mnemonic.deriveKey(addressIndex);
const userWallet = UserWallet.fromSecretKey({ secretKey, password });
const jsonFileContent = userWallet.toJSON();

fs.writeFileSync("myKeyFile.json", JSON.stringify(jsonFileContent));
```

## Got it from multiversx official documentation [here](https://docs.multiversx.com/developers/creating-wallets/).
