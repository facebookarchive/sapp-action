# SAPP Github Action
[![test](https://github.com/facebook/sapp-action/actions/workflows/test.yml/badge.svg)](https://github.com/facebook/sapp-action/actions/workflows/test.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

SAPP Github Action allows you run [SAPP (Static Analysis Post Processor)](https://github.com/facebook/sapp#sapp) in CI to post process static analysis results from tools like [Pysa](https://github.com/facebook/pyre-check) and [Mariana Trench](https://github.com/facebook/mariana-trench/).

SAPP Action will upload the results after applying [filters](https://github.com/facebook/sapp#filters) in SARIF to GitHub, where you can view them in the Security tab of your repo.

## Usage
```yml
# .github/workflows/test.yml

- name: Saving static analysis results for SAPP
    uses: actions/upload-artifact@v2
    with:
        name: static-analysis-results
        path: ./path/to/static-analysis-output
        if-no-files-found: error

- name: Postprocess static analysis results
  uses: facebook/sapp-action@main
  with:
    version: latest # version of fb-sapp on PyPi you want to use
    artifact-handle: static-analysis-results
    filters-directory: /path/to/sapp/filters
```

## License

SAPP Action is licensed under the MIT license.
