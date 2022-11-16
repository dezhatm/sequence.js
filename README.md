0xsequence
==========

[Sequence](https://sequence.xyz): simple & powerful Ethereum development stack and smart wallet.

## Usage

`npm install 0xsequence ethers`

or

`pnpm install 0xsequence ethers`

or

`yarn add 0xsequence ethers`


## Packages

- [0xsequence](./packages/0xsequence)
- [@0xsequence/abi](./packages/abi)
- [@0xsequence/api](./packages/api)
- [@0xsequence/auth](./packages/auth)
- [@0xsequence/config](./packages/config)
- [@0xsequence/deployer](./packages/deployer)
- [@0xsequence/guard](./packages/guard)
- [@0xsequence/multicall](./packages/multicall)
- [@0xsequence/network](./packages/network)
- [@0xsequence/provider](./packages/provider)
- [@0xsequence/relayer](./packages/relayer)
- [@0xsequence/transactions](./packages/transactions)
- [@0xsequence/utils](./packages/utils)
- [@0xsequence/wallet](./packages/wallet)


## Development Environment

Below are notes and instructions on how to get your development environment up and running,
and enjoyable.

1. **Install dependencies** -- we use yarn workspaces, so please use yarn instead of npm.
   Run, `yarn install`

2. **Workflow** -- we use the amazing [preconstruct](https://github.com/preconstruct/preconstruct)
   package to handle our monorepo build system.

3. **Local dev** -- when you're working on the code in this repository, you can safely run
   `yarn dev` at the root-level, which will link all packages/** together, so that when a
   local dependency from packages/** is used by another, it will automatically be linked
   without having to run a build command. Just remember: run `yarn dev` anytime you developing
   in this repo. Note, that when you run `yarn build` it will clear the dev environment, so
   you will need to run `yarn dev` again after a build. However, `yarn build` should only be
   used when making a release.

4. **Testing** -- to test the system, you can run `yarn test` at the top-level or at an individual
   package-level.

5. **Type-checking** -- to typecheck the system you can run `yarn typecheck` at any level.

6. **Building** -- to _compile_ the project to dist files for a release, run `yarn build` at
   the root-level. Note building packages repeatedly during development is unnecessary with
   `preconstruct`. During local development run `yarn dev` and when building to make a release,
   run `yarn build`.

7. **Versioning** -- this repository uses the handy [changesets](https://github.com/atlassian/changesets)
   package for package versioning across the monorepo, as well as changelogs. See _Releasing_ section below.


## Releasing to NPM

0xsequence uses changesets to do versioning. This makes releasing really easy and changelogs are automatically generated.

### How to do a release

1. Run `yarn` to make sure everything is up to date
2. Code.. do your magic
3. Run `yarn changeset` to generate a new .changeset/ entry explaining the code changes
4. Version bump all packages regardless of them having changes or not
5. Commit and submit your changes as a PR for review
6. Once merged and you're ready to make a release, continue to the next step. If you're not
   ready to make a release, then go back to step 2.
7. Run `yarn build && yarn test` to double check all tests pass
8. Run `yarn version-packages` to bump versions of the packages
9. Commit files after versioning. This is the commit that will be published and tagged: `git push --no-verify`
10. Run `yarn release`. If the 2FA code timesout while publishing, run the command again
    with a new code, only the packages that were not published will be published.
11. Finally, push your git tags, via: `git push --tags --no-verify`


## How to do a snapshot release

NOTE: snapshot release is for dev preview, it's similar to the above, but:

1. `yarn changeset`
2. `yarn changeset version --snapshot`
3. `yarn changeset publish --tag snapshot`


## NOTES

1. Browser tests can be run with `yarn test` or, separately `yarn test:server` and `yarn test:run`
2. To run a specific test, run `yarn test:only <test-file-basename>`, ie. `yarn test:only window-transport`


## TIPS

* If you're using node v18+ and you hit the error `Error: error:0308010C:digital envelope routines::unsupported`,
  make sure to first set, `export NODE_OPTIONS=--openssl-legacy-provider`


## LICENSE

Apache-2.0

Copyright (c) 2017-present Horizon Blockchain Games Inc. / https://horizon.io
