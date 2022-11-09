# Sync up to AWS CodeCommit Action

Synchronize from GitHub repository to AWS CodeCommit via GitHub Actions.  
No need to ssh-private-key. Need to AWS IAM Credentials only.

## Example usage

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
          aws-access-key-id: ${{ secrets.Github_Codecommit_AWS_KEY }}
          aws-secret-access-key: ${{ secrets.GitHub_Codecommit_AWS_SECRET_KEY }}
          aws-region: eu-west-1

      - name: Sync up to CodeCommit
        uses: nsannsri/awssync@v1
        with:
          repository_name: name_aws_codecommit_repo
          aws_region: eu-west-1
```

## Inputs

- `repository_name` **Required** CodeCommit repository name.
- `aws_region` **Required** Region of the CodeCommit repository.

## License

[MIT](LICENSE)

## Author

[youyo](https://github.com/youyo)
