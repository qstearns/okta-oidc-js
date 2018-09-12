# Contributing to Okta Open Source Repos

Thank you for your interest in contributing to Okta's Open Source Projects! Before submitting a PR, please take a moment to read over our [Contributer License Agreement](https://developer.okta.com/cla/). In certain cases, we ask that you [sign a CLA](https://developer.okta.com/sites/all/themes/developer/pdf/okta_individual_contributor_license_agreement_2016-11.pdf) before we merge your pull request.

## Style

### Git Commit Messages

We use an adapted form of [Conventional Commits](http://conventionalcommits.org/).

  * Use the present tense ("Adds feature" not "Added feature")
  * Limit the first line to 72 characters or less
  * Add one feature per commit. If you have multiple features, have multiple commits.

#### Template

    <type>: Short Description of Commit
    <BLANKLINE>
    (Optional) More detailed description of commit
    <BLANKLINE>
    (Optional) Resolves: <Jira # or Issue #>

#### Template for specific package change

    <type>[<package-name>]: Short Description of Commit
    <BLANKLINE>
    (Optional) More detailed description of commit
    <BLANKLINE>
    (Optional) Resolves: <Jira # or Issue #>

#### Type
Our types include:
  * `feat` when creating a new feature
  * `fix` when fixing a bug
  * `test` when adding tests
  * `refactor` when improving the format/structure of the code
  * `docs` when writing docs
  * `release` when pushing a new release
  * `chore` others (ex: upgrading/downgrading dependencies)

#### Example
    docs: Updates CONTRIBUTING.md

    Updates Contributing.md with new emoji categories
    Updates Contributing.md with new template

    Resolves: #1234

#### Example for specific package change
    fix[okta-angular]: Fixes bad bug

    Fixes a very bad bug in okta-angular

    Resolves: #5678

#### Breaking changes

  * Breaking changes MUST be indicated at the very beginning of the body section of a commit. A breaking change MUST consist of the uppercase text `BREAKING CHANGE`, followed by a colon and a space.
  * A description MUST be provided after the `BREAKING CHANGE:`, describing what has changed about the API.

#### Example for a breaking change

    feat: Allows provided config object to extend other configs

    BREAKING CHANGE: `extends` key in config file is now used for extending other config files

## Running Tests locally

You can run tests is each individual package by navigating to the package and running `npm test`.
E.g:

```bash
# At project root
cd packages/oidc-middleware
npm install
npm test
```

You can also run all the tests inside each of the packages from the project root.

For that, you will need to install the dependencies of each package. This can be performed via the following commands:

```bash
# At project root
npm install
npm run bootstrap
```

> **Note:** Since the packages contain libraries for both Single-Page applications and Web Applications, you will need to create an SPA and Web App in your okta org.
>
> For the SPA, set the following login redirect URIs - `http://localhost:8080/implicit/callback` & `http://localhost:3000/implicit/callback`
>
> For the Web App, set the following login redirect URI - `http://localhost:8080/authorization-code/callback`

Next, setup the following environment variables:

```bash
export ISSUER=https://{your-okta-org-url}/oauth2/default
export SPA_CLIENT_ID={yourSPAClientId}
export WEB_CLIENT_ID={yourWebAppClientId}
export CLIENT_SECRET={yourWebAppClientSecret}
export USERNAME={yourOktaOrgLoginName}
export PASSWORD={yourOktaOrgLoginPassword}
```

After setting up the environment variables, run the following command to run all tests in the packages

```bash
npm test
```
