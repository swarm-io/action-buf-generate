# Buf generate action
This action installs buf, some protoc and grpc dependencies, runs `buf generate`, and pushes changes if `push` is true. This is a public action but is set up for our use case specifically so may not work for everyone.

This action's defaults are set up to be run on the `pull_request` event, and push back to the source branch, so that new pbs are generated

## Inputs

| Name | Description | Required | Default |  
| - | - | - | - |
| push | Should changes be pushed | False | True |
| branch | Git branch name where changes should be pushed to | False | ${{ github.head_ref }} |


## Example usage

```yaml  
name: Bump version  
on:  
  pull_request:  
    branches:  
      - main  
jobs:  
  buf-generate:  
  name: Run buf generate  
  runs-on: ubuntu-latest  
  steps:  
 - name: Checkout  
      uses: actions/checkout@v2  
    - name: Buf generate  
      uses: swarm-io/action-buf-generate@v1
```
