# GitHub Action: Workflow Run Queue

If the same workflow is already running from a previous commit, wait for it to finish

[![license][license-img]][license-url]
[![release][release-img]][release-url]

<details>
  <summary><strong>Why?</strong></summary>

Workflows run on every commit asynchronously, this is fine for most cases, however, you might want to wait for a previous commit workflow to finish before running another one, some example use-cases:

- Deployment workflows
- Terraform workflows
- Database Migrations

</details>

## Usage

###### `.github/workflows/my-workflow.yml`

``` yaml
jobs:
  xyz:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - uses: khulnasoft/action-workflow-queue@v1

      # only runs additional steps if there is no other instance of `my-workflow.yml` currently running
```

### Inputs

| input          | required | default        | description                                     |
|----------------|----------|----------------|-------------------------------------------------|
| `github-token` | ❌       | `github.token` | The GitHub token used to call the GitHub API    |
| `timeout`      | ❌       | `600000`       | timeout before we stop trying (in milliseconds) |
| `delay`        | ❌       | `10000`        | delay between status checks (in milliseconds)   |

----
> Author: [KhulnaSoft Ltd](https://www.khulnasoft.com/) &bull;
> Twitter: [@khulnasoft](https://twitter.com/khulnasoft)

[license-url]: LICENSE
[license-img]: https://badgen.net/github/license/khulnasoft/action-workflow-queue

[release-url]: https://github.com/khulnasoft/action-workflow-queue/releases
[release-img]: https://badgen.net/github/release/khulnasoft/action-workflow-queue
