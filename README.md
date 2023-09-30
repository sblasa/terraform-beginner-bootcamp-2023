# Terraform Beginner Bootcamp 2023

## Semantic Versioning :mage:

This project is going utilize semantic versioning for its tagging.
[semver.org](https://semver.org/)

The general format:
**MAJOR.MINOR.PATCH**, eg. `1.0.1`

- **MAJOR** version when you make incompatible API changes
- **MINOR** version when you add functionality in a backward compatible manner
- **PATCH** version when you make backward compatible bug fixes
- Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

## Install the Terraform CLI

### Considerations with the Terraform CLI Changes
The Terraform CLI instructions have changed due to gpg keyring changes. So we needed to refer to the latest install CLI instructions via Terraform Documentation and change the scripting for install.

This bash script is located here: [./bin/install_terraform_cli](./bin/install_terraform_cli)

### Considerations for Linux Distribution

This project is built against Ubuntu.
Please consider checking your Linux Distribution and change accordingly to distribution needs.
[How To Check OS Version in Linux](https://www.cyberciti.biz/faq/how-to-check-os-version-in-linux-command-line/)

Example of checking OS version:

```
$ cat /etc/os-release
PRETTY_NAME="Ubuntu 22.04.3 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.3 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
```

### Refactoring into Bash Scripts

While fixing the Terraform CLI gpg depreciation issues, we noticed that bash scripts steps were a considerable amount of more code, so we decided to create a bash script to install the Terraform CLI.

- This will keep the Gitpod Task file ([gitpod.yml](.gitpod.yml)) tidy.
- This will allow us an easier way to debug and excute manually Terraform CLI in Gitpod
- This will allow better porbability for other projects that need to install Terraform CLI.


[Install Terraform CLI](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)


#### Shebang Considerations

A Shebang (prounced Sha-bang) tells the bash script what parogram that will interpret the script. eg. `#!/bin/bash`

ChatGPT recommended this format for bash: `#!/usr/bin/env bash`

- for portability for different distributions
- will search user's PATH for the bash executable

#### Execution Considerations

When executing bash script, we can use the `./` shorthand notation to execute the bash script.

eg. `./bin/install_terraform_cli`

If we are using a script in .gitpod.yml. We need to point the script to a program to interpret it.
eg. `sourc .bin/install_terraform_cli`


[Shebang Unix](https://en.wikipedia.org/wiki/Shebang_(Unix))

#### Linux Permissions Considerations

In order make our bash scripts executable, we need to change Linux permissions for the file to be executable at the user mode.

```sh
chmod u+x ./bin install_terraform_cli
```

alternatively;

```sh
chmod 744 ./bin install_terraform_cli
```


https://en.wikipedia.org/wiki/Chmod

### Gitpod Lifecycle (Before, Init, Command)

We need to be careful when using the IOnit becuase it will not rerun if we restart an existing workspace.


https://www.gitpod.io/docs/configure/workspaces/tasks