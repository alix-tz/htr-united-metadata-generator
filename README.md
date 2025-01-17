# HUM Generator, the HTR United Metadata Generator
Tool that generates, through github actions, a set of metadata to help document repos.

# Install as github action

In the directory .github/workflows, create a file HumGenerator with the following content

```yaml
# This workflow will install Python dependencies, run tests and lint with a single version of Python
# For more information see: https://help.github.com/actions/language-and-framework-guides/using-python-with-github-actions

name: HTR United Report

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Set up Python 3.8
      uses: actions/setup-python@v2
      with:
        python-version: 3.8
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install https://github.com/HTR-United/htr-united-metadata-generator/archive/refs/heads/main.zip
    - name: Run Report
      run: |
        humGenerator --group **/*.xml
```

