# Secret Scanning

This repository contains sample implementation for secret scanning using gitleaks. 

## Installation

https://github.com/zricethezav/gitleaks 

```
brew install gitleaks
```

## Running secret scanning

```
gitleaks detect 
```

## Pre-commit hook

```
pre-commit install
```

Note: uses .pre-commit-config.yaml file

## Github action

```
name: gitleaks
on: [pull_request, push, workflow_dispatch]
jobs:
  gitleaks-scan:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Run gitlakes docker	    
      uses: docker://zricethezav/gitleaks
      with:
        args: detect --source /github/workspace/ --no-git --verbose
```
Sample github action is included with this repo.