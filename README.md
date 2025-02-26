<div align="center">
  <img width="300" src="https://github.com/grantbirki/link/blob/main/docs/assets/logo.png" /> <br>
  <sub>Logo by <a href="https://www.instagram.com/malohff">@malohff</a></sub>
</div>

# link

[![link](https://github.com/GrantBirki/link/actions/workflows/link.yml/badge.svg)](https://github.com/GrantBirki/link/actions/workflows/link.yml)
[![json-yaml-validate](https://github.com/GrantBirki/link/actions/workflows/json-yaml-validate.yml/badge.svg)](https://github.com/GrantBirki/link/actions/workflows/json-yaml-validate.yml)

My personal [`action-ln`](https://github.com/nobe4/action-ln) config for linking various files between repositories.

## Usage

Here is an example of linking a file from one repository to another:

```yaml
links:
  - from:
      repo: grantbirki/ruby-template
      path: script/bootstrap
    to:
      repo: grantbirki/ldap-api
      path: script/bootstrap
```

Now this will operate in a similar manner to dependabot. If a change takes place to the `script/bootstrap` file in the `grantbirki/ruby-template` repository, the next time the `nobe4/action-ln` workflow runs, it will open a pull request to update the `script/bootstrap` file in the `grantbirki/ldap-api` repository.

## Authentication

I am using a GitHub App to authenticate through the `nobe4/action-ln` Action. This GitHub App has the following permissions:

- Contents: **Read & Write**
- Pull Requests: **Read & Write**

I have it configured to only have permissions on certain repositories. If I want to add a new repository to this configuration (to have files synced **to** it), then I need to update the list of repositories that my GitHub App has access to. This can be done on the [GitHub App settings page](https://github.com/settings/installations/61743951) (by myself only of course).

If the repository that the file is being synced **from** is private, then the GitHub App will also need to be added to that repo as well. If it is public, then no further action is needed since the GitHub App requires no extra permissions to read public repositories.
