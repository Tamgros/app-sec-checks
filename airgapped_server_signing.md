# Airgapped server signing

1. [Problem](#problem)
2. [Overview](#overview)
3. [Code Mocks](#code-mocks)
4. [Next Steps](#next-steps)

# TODO https://www.notion.so/solanafoundation/Security-DeFi-group-review-process-8293b3a199c94b43a1f576cd093dc306

## Problem

Some applications provide a much better UX if a server is automating signatures, but this poses security risks when keys that control funds are being controlled by a service that is connected to the internet.

Common examples of this is a centralized exchanges signing for withdraws or a video game signing for mints of items.

## Overview
This article will talk about the security around automatic server authoritative signing.

### Air Gap Signing [Wikipedia on Air Gap networking](https://en.wikipedia.org/wiki/Air_gap_(networking))

Your main signing service should not be connected to the open internet. Instead, your server should call the signing service through a white listed connection. Some providers provide tools for the server to connect externally through gateways, but still connect to internal services in a VPN

- Only interface to the API should be through a secure whitelisted enpoint
  
### API design 
- Business logic separate from signing
- Highly specific function parameters, like orn
    - checks: 
    - not just types, also ranges
    - consider interactions where appropriate

The API parameters should be well defined and the functions should be scoped for specific functionality. ie, instead of

```typescript
async function transfer(transfer): Promise<web>

```

```typescript
import * as web3 from '@solana/web3'
import * as token from '@solana/spl-token'

async function buildTransferTransaction(
    source: web3.PublicKey,
    destination: web3.PublicKey,
    owner: web3.PublicKey,
    amount: number
): Promise<web3.Transaction> {
    const transaction = new web3.Transaction().add(
        token.createTransferInstruction(
            source,
            destination,
            owner,
            amount,
        )
    )

    return transaction
}


```
  
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


### Code Mocks



## Next Steps

