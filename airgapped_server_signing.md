# Airgapped server signing

1. [Problem](#problem)
2. [Overview](#overview)
3. [API Design](#api-design)
4. [Next Steps](#next-steps)

## TODO https://www.notion.so/solanafoundation/Security-DeFi-group-review-process-8293b3a199c94b43a1f576cd093dc306

## Problem

Some applications provide a much better UX if a server is automating signatures, but this poses security risks when keys that control funds are being controlled by a service that is connected to the internet.

Common examples of this is a centralized exchanges signing for withdraws or a video game signing for mints of items.

## Overview
This article will talk about the security around automatic server authoritative signing.

### "Air Gap Signing" [Wikipedia on Air Gap networking](https://en.wikipedia.org/wiki/Air_gap_(networking))

Ok, so this isn't completely air gapped, but I'm exaggering to get your attention. Your main signing service should not be connected to the open internet. Instead, your server should call the signing service through a white listed connection. Some providers provide tools for the server to connect externally through gateways, but still connect to internal services in a VPN

- Only interface to the API should be through a secure whitelisted enpoint
  
### API design 
- Business logic separate from signing
- Highly specific function parameters, like orn
    - checks: 
    - not just types, also ranges
    - consider interactions where appropriate

The API parameters should be well defined and the functions should be scoped for specific functionality. ie, instead of a generic

```typescript
async function signTransfer(transactionToSign): Promise<TransactionSignature> {
    ...
};

```
Instead, be very explicit: 
- parameters 
  - The types of the parameters
  - Check parameter expectations
- be specific with the methods being signed

Get as granular as possible. If you have different types of transfers, name them explicitly with the appropriate checks and probably even have them have them be different methods. 

**Instead of the above flexible function, this would be better**

```typescript

var whiteList Array<publicKey> = []: 

async function signWhitelistTransfer(
    ...
    toTokenAccount: tokenAccount,
    amount: number
): Promise<TransactionSignature> {
    Assert(whiteList.includes(toTokenAccount.address));

    Assert( someCondition(amount));
    ...
}

async function signHundredTokenTransfer(
    ...
    amount: number
): Promise<TransactionSignature> {

    Assert( amount == 100);
    ...
}

```

This should also be reflected in the API design. 
```javascript
app.post('/signWhitelistTransfer', (req, res) => {
    // req should contain the exact info
});

app.post('/signHundredTokenTransfer', (req, res) => {
    // req should contain the exact info
});
```



// https://soldev.app/course/token-program
  
### Code contribution 
- [Give Contributors least permissions to do their work](https://en.wikipedia.org/wiki/Principle_of_least_privilege#:~:text=The%20principle%20means%20giving%20a,backup%20and%20backup%2Drelated%20applications.)

###  Limits (spending) and alerts
- rate limits
- ratios
- 
Hot-Cold wallet
Testing?

Misc
- offline signing
- use RPC
- HD wallets




## Next Steps

