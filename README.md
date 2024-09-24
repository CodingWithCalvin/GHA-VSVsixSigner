# codingwithcalvin/action-vs-vsix-signer

Github Action to sign your Visual Studio extensions before you publish to the marketplace

## Usage

You can use the Visual Studio VSIX Signer GitHub Action by configuring a YAML-based workflow file, e.g. .github/workflows/deploy.yml.

> *This action only works on a Windows-based runner*

## Sign a local VSIX File

```yml
steps:
    - name: Checkout
      uses: actions/checkout@v2

    - name: Visual Studio VSIX Signer
      uses: codingwithcalvin/action-vs-vsix-signer@v1
      with:
        # REQUIRED
        sign-certificate-path: ./src/SigningCert.snk
        vsix-path: ./src/outputFolder/Extension.vsix
        sign-password: ${{ secrets.signpassword }}
        
        # OPTIONAL
        vs-version: latest
        vs-prerelease: false
```

## Inputs

| Input                 | Required | Description                                                                                                          |
| --------------------- | -------- | -------------------------------------------------------------------------------------------------------------------- |
| sign-password         | Y        | Your password to utilize the supplied signing certificate                                                            |
| sign-certificate-path | Y        | Path to the certificate used to sign the VSIX file                                                                   |
| vsix-path             | Y        | Path to the local VSIX package you wish to publish                                                                   |
| vs-version            | N        | Specify the exact version of Visual Studio tooling to use; default to `latest`                                       |
| vs-prerelease         | N        | Allow a pre-release installation of Visual Studio tooling; default to `false`                                        |
