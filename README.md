# Vault Factory


## Settings
This is a generic settings contract to be owned by governance. It allow to control and set parameters for all contracts

## Vault Factory
This contract is to mint vault, each time when user call mint function and the user must pass in:
- an ERC20 token name
- an ERC20 token symbol
- the ERC721 token address they wish to fractionalize
- the ERC721 token id they wish to fractionalize
- the desired ERC20 token supply
- the initial listing price of the NFT
- their desired curator fee

This contract also have updateMaximum_supply function to update the supply of the ERC20 token to fractionize into.


## Token Vault
The token vault is the smart contract which holds the logic for NFTs that have been fractionalized.


Alongside this logic, is auction logic which allows for an outside user to initial a buyout auction of the NFT. Here there are `start`, `bid`, `end` and `cash` functions.
#### Start
The function called to kick off an auction. `msg.value` must be greater than or equal to the current reserve price.
#### Bid
The function called for all subsequent auction bids.
#### End
The function called when the auction timer is up and ended.
#### Cash
The function called for token holders to cash out their share of the ETH used to purchase the underlying NFT.

There is also some admin logic for the `curator` (user who initially deposited the NFT). They can reduce their fee or change the auction length. Alongside this, they are able to claim fees in the form of token supply inflation.

## IndexERC721
This is a single token ERC721 which is used to custody multiple ERC721 tokens. 
#### depositERC721
Anyone can deposit an ERC721 token into the contract
#### withdrawERC721
The token holder can withdraw any ERC721 tokens in the contract
#### withdrawETH
The token holder can withdraw any ETH in the contract
#### withdrawERC20
The token holder can withdraw any ERC20 token in the contract

## ERC721_token_create 

This is sample contract to create token for testing , can be neglected if not required

## IndexERC721Factoy
This contract have the logic to create bakset token using IndexERC721.

####createBasket
It simply create basket and emits it

# Deployment Procedure

## Deploy ERC721Vault Factory

To deploy this contract, one need to depoly the settings.sol first as this will take settings address to deploy

Than we can deploy ERC721Vault Factory

## Deploy IndexERC721Factory

To deploy this contract, we just need deploy to this one . its independent.

### NOTE: 

This project is directly import openzepin file for now, once everything is good we can make a local directly for openzeplin from github.