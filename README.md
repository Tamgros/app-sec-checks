# app-sec-checks
> The goal of this list is to have a common framework to view up and downstream projects' security. A good example of this would be interacting with an external partner. Each project isn't necessarily doing BD in isolation, there is an ecosystem of collaborative projects.

> In the good case, Solana can show off network effects. In the negative case, many "points of failure" can be intimidating. This doc is here to lower that barrier.

## Linked pages
- [ ] Bug bounties clear and explicit 
- [ ] Open source, published ABI
- [ ] Audit Docs

## Add Verifiable information
- [ ] [Upgrade Authority Best practices](https://blog.neodyme.io/posts/solana_upgrade_authority/)
  - [ ] Squads multisig - Stepan Simkin (guide?)
- [ ] Devnet implementation
- [ ] Client SDKs, if front end gets hacked, need to be able to execute through sdk
- [ ] Verifiabile builds. [Example from Eclipse](https://github.com/Ellipsis-Labs/solana-verifiable-build)


## Description needed
- [ ] Paths to immutable/soft frozen

## best practices
### Off chain
- [ ] Pager duty 
- [ ] Circuit breaker, freeze ability on attack
- [ ] Treasury abstracted away
- [ ] [Airgapped signing](https://github.com/Tamgros/app-sec-checks/blob/main/airgapped_server_signing.md)

### On chain Code
  ((request for checklist, here's some inspo ))  
[neodyme's audit prep](https://github.com/neodyme-labs/solana-security-txt)  
[neodyme's common pitfalls](https://blog.neodyme.io/posts/solana_common_pitfalls/)


## CI/CD:
- [ ] Text searches for any private keys
- [ ] Sec3 tools with CI/CD



## Situationally relevant
- [ ]  Econ vulnerabilities
  - [ ]  [Gauntlet](https://gauntlet.network/)
  - [ ]  [20 squares](https://20squares.xyz/) (not yet Solana)


## Process
Open a github issue with the checklist  
- [https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists)

## Extra credit
- [ ] Formal verification (https://twitter.com/squadsprotocol/status/1618671630359887873?s=46&t=-oVDphlUuRY-yldrtuWokQ)


Jiri had a great suggestion
- Turn this into a community driven discussion


## Discusion
- risks - security theater. Wastes time and doesn't actually increase secruity
- Who reviews authentically?
  - v0 - self review with informal signoff
  - v1 - some sort of DAO vote? POA? Just need some display of certification, would be great if it's communal.

TODO
- external "approvals"
- explore putting it as a standard template
- Part of anchor init?
- Part of the explorer verification process
- Client/user side best practices
- cold-hot wallet with top ups and time delay
