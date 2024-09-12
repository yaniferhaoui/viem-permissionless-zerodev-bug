# NestJS compilation error with viem + permissionless.js + zerodev sdk

## Installation

```bash
$ yarn install
```

## Running the app and watch the compilation errors

```bash
nest start --watch
```

## Examples of returned compilation errors

```bash
...

node_modules/permissionless/actions/smartAccount/sendTransaction.ts:97:36 - error TS2339: Property 'account' does not exist on type 'never'.
  The intersection 'Client<Transport, TChain, TAccount>' was reduced to 'never' because property 'cacheTime' has conflicting types in some constituents.

97         account: account_ = client.account,
                                      ~~~~~~~

node_modules/permissionless/actions/smartAccount/sendTransactions.ts:92:39 - error TS2344: Type 'TAccount' does not satisfy the constraint 'Account'.
  Type 'SmartAccount<entryPoint, string, TTransport, TChain>' is not assignable to type 'Account'.
    Type 'SmartAccount<entryPoint, string, TTransport, TChain>' is not assignable to type '{ address: `0x${string}`; nonceManager?: NonceManager; sign?: (parameters: { hash: `0x${string}`; }) => Promise<`0x${string}`>; experimental_signAuthorization?: (parameters: Authorization) => Promise<...>; ... 17 more ...; isDeployed?: undefined; }'.
      Types of property 'client' are incompatible.
        Type 'Client<TTransport, TChain, undefined, PublicRpcSchema, PublicActions<TTransport, TChain>>' is not assignable to type 'undefined'.
          Type 'TAccount' is not assignable to type '{ address: `0x${string}`; nonceManager?: NonceManager; sign?: (parameters: { hash: `0x${string}`; }) => Promise<`0x${string}`>; experimental_signAuthorization?: (parameters: Authorization) => Promise<...>; ... 17 more ...; isDeployed?: undefined; }'.
            Type 'SmartAccount<entryPoint, string, TTransport, TChain>' is not assignable to type '{ address: `0x${string}`; nonceManager?: NonceManager; sign?: (parameters: { hash: `0x${string}`; }) => Promise<`0x${string}`>; experimental_signAuthorization?: (parameters: Authorization) => Promise<...>; ... 17 more ...; isDeployed?: undefined; }'.
              Types of property 'client' are incompatible.
                Type 'Client<TTransport, TChain, undefined, PublicRpcSchema, PublicActions<TTransport, TChain>>' is not assignable to type 'undefined'.

92     client: Client<Transport, TChain, TAccount>,
                                         ~~~~~~~~

node_modules/permissionless/actions/smartAccount/sendTransactions.ts:103:36 - error TS2339: Property 'account' does not exist on type 'never'.
  The intersection 'Client<Transport, TChain, TAccount>' was reduced to 'never' because property 'cacheTime' has conflicting types in some constituents.

103         account: account_ = client.account,
                                       ~~~~~~~
...

node_modules/viem/utils/signature/hashTypedData.ts:151:44 - error TS2345: Argument of type 'unknown[]' is not assignable to parameter of type '(readonly (readonly (readonly (readonly (readonly (readonly (readonly (readonly (readonly (readonly (readonly ...[])[])[])[])[])[])[])[])[])[])[] | readonly (readonly (readonly (readonly (readonly any[])[])[])[])[])[]'.
  Type 'unknown' is not assignable to type 'readonly (readonly (readonly (readonly (readonly (readonly (readonly (readonly (readonly (readonly (readonly ...[])[])[])[])[])[])[])[])[])[])[] | readonly (readonly (readonly (readonly (readonly any[])[])[])[])[]'.

151   return encodeAbiParameters(encodedTypes, encodedValues)
                                               ~~~~~~~~~~~~~

node_modules/viem/utils/transaction/parseTransaction.ts:295:5 - error TS2322: Type 'ToBlobSidecarsReturnType<"bytes" | "hex">' is not assignable to type 'false | readonly BlobSidecar<`0x${string}`>[]'.
  Type 'BlobSidecars<Uint8Array>' is not assignable to type 'false | readonly BlobSidecar<`0x${string}`>[]'.
    Type 'BlobSidecar<Uint8Array>[]' is not assignable to type 'readonly BlobSidecar<`0x${string}`>[]'.
      Type 'BlobSidecar<Uint8Array>' is not assignable to type 'BlobSidecar<`0x${string}`>'.
        Type 'Uint8Array' is not assignable to type '`0x${string}`'.

295     transaction.sidecars = toBlobSidecars({
        ~~~~~~~~~~~~~~~~~~~~

node_modules/viem/utils/transaction/serializeTransaction.ts:248:7 - error TS2322: Type 'ToBlobSidecarsReturnType<"bytes" | "hex">' is not assignable to type 'false | readonly BlobSidecar<`0x${string}`>[]'.
  Type 'BlobSidecars<Uint8Array>' is not assignable to type 'false | readonly BlobSidecar<`0x${string}`>[]'.
    Type 'BlobSidecar<Uint8Array>[]' is not assignable to type 'readonly BlobSidecar<`0x${string}`>[]'.
      Type 'BlobSidecar<Uint8Array>' is not assignable to type 'BlobSidecar<`0x${string}`>'.
        Type 'Uint8Array' is not assignable to type '`0x${string}`'.

248       sidecars = toBlobSidecars({ blobs, commitments, proofs })
          ~~~~~~~~

[5:38:52 PM] Found 322 errors. Watching for file changes.
```
