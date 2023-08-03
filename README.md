# Combo Chain Token List

The Combo Chain token list is a list of tokens managed by the maintainers of this repo that have been deployed on Combo Chain.

Please note that by adding a token to the list we aren’t making any claims about the token itself; tokens are not reviewed for their quality, merits, or soundness as investments.

## Review process and merge criteria

### Process overview

1. Follow the instructions below to create a PR that would [add your token to the list](#adding-a-token-to-the-list).
2. Wait for a reviewer to kick off the [automated checks](#automated-checks).
3. After the automated checks pass and a reviewer approves the PR, then it will automatically be merged.

**Note:** The standard bridge does *not* support certain ERC-20 configurations:

- [Fee on transfer tokens](https://github.com/d-xo/weird-erc20#fee-on-transfer)
- [Tokens that modify balances without emitting a Transfer event](https://github.com/d-xo/weird-erc20#balance-modifications-outside-of-transfers-rebasingairdrops)


## Adding a token to the list

### Create a folder for your token

Create a folder inside of the [data folder](https://github.com/ComboLabs/ComboTokenList/tree/master/data) with the same name as the symbol of the token you are trying to add. For example, if you are adding a token with the symbol "ETH" you must create a folder called ETH.

### Add a logo to your folder


Add a logo to the data folder you just created. Your logo MUST be an SVG called `logo.svg` or `logo.png`. Your logo should be at least 200x200 pt minimum and 256x256 pt preferred.


### Create a data file

Add a file to your folder called `data.json` with the following format:

```json
{
  "name": "Token Name",
  "symbol": "SYMBOL",
  "decimals": 18,
  "description": "A Combo Chain token",
  "website": "https://token.com",
  "twitter": "@token",
  "tokens": {
    "combo": {
      "address": "0x1234123412341234123412341234123412341234"
    }
  }
}
```

#### Per-token overrides

If you require overrides for specific tokens, you can include the `overrides` field. You are able to override the `name`, `symbol`, `decimals`, or `bridge` for any token. You do not need to override every token at the same time.

```json
{
  "name": "Token Name",
  "symbol": "SYMBOL",
  "decimals": 18,
  "description": "A Combo Chain token",
  "website": "https://token.com",
  "twitter": "@token",
  "tokens": {
    "combo": {
      "address": "0x1234123412341234123412341234123412341234",
      "overrides": {
        "name": "My Ethereum Token"
      }
    }
  }
}
```


### Create a pull request

Open a [pull request](https://github.com/ComboLabs/ComboTokenList/pulls) with the changes that you've made. Please only add one token per pull request to simplify the review process. This means two new files inside of one new folder. If you want to add multiple tokens, please open different PRs for each token.

### Respond to validation checks

Your pull request will be validated by a series of automated checks. If one of these checks fails, please resolve these issues and make sure that validation succeeds. We will review your pull request for final approval once automated validation succeeds.

### Wait for the token list to update automatically

Once your PR is merged, the token list will update automatically to include your token. Please do NOT update the token list (`combo.tokenlist.json`) directly. All token list updates will be handled automatically when PRs are merged into the `master` branch.
