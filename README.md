
## Usage

```yaml
name: GitHub to Codecommit Sync

on:
  push:
    tags-ignore:
      - '*'
    branches:
      - 'master'

jobs:
  sync:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
        with:
          fetch-depth: 0

      - name: Configure AWS Credentials
        uses: aws-actions/configure-aws-credentials@v1
        with:
          aws-access-key-id: ${{ secrets.GH_CC_AWS_KEY  }}
          aws-secret-access-key: ${{ secrets.GH_CC_AWS_SECRET_KEY }}
          aws-region: eu-west-1

      - name: Sync up to CodeCommit
<<<<<<< HEAD
        uses: dms-jovan-stanoevski/githubsync@main
=======
        uses: dms-jovan-stanoevski/githubsync@v1
>>>>>>> e6d73fe5f8768f0e1f691e0053dbdb209810087b
        with:
          repository_name: maksystem-internal-github-backup
          aws_region: eu-west-1
```
