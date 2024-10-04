# SonarQube GitHub Action

![](https://i.imgur.com/waxVImv.png)
### [View all Roadmaps](https://github.com/nholuongut/all-roadmaps) &nbsp;&middot;&nbsp; [Best Practices](https://github.com/nholuongut/all-roadmaps/blob/main/public/best-practices/) &nbsp;&middot;&nbsp; [Questions](https://www.linkedin.com/in/nholuong/)

Using this GitHub Action, scan your code with SonarQube scanner to detects bugs, vulnerabilities and code smells in more than 20 programming languages!

SonarQube is an open-source platform developed by SonarSource for continuous inspection of code quality to perform automatic reviews with static analysis of code to detect bugs, code smells, and security vulnerabilities on 20+ programming languages.

## Requirements

* [SonarQube server](https://docs.sonarqube.org/latest/setup/install-server/).
* That's all!

## Usage

The workflow, usually declared in `.github/workflows/build.yaml`, looks like:

```yaml
on:
  # Trigger analysis when pushing in master or pull requests, and when creating
  # a pull request. 
  push:
    branches:
      - master
  pull_request:
      types: [opened, synchronize, reopened]

name: SonarQube Scan
jobs:
  sonarqube:
    name: SonarQube Trigger
    runs-on: ubuntu-latest
    steps:
    - name: Checking out
      uses: actions/checkout@master
      with:
        # Disabling shallow clone is recommended for improving relevancy of reporting
        fetch-depth: 0
    - name: SonarQube Scan
      uses: nholuongut/sonarqube-action@v1.2.0
      with:
        host: ${{ secrets.SONARQUBE_HOST }}
        login: ${{ secrets.SONARQUBE_TOKEN }}
```

You can change the analysis base directory and/or project key by using the optional input like this:

```yaml
uses: nholuongut/sonarqube-action@master
with:
  host: ${{ secrets.SONARQUBE_HOST }}
  login: ${{ secrets.SONARQUBE_TOKEN }}
  projectBaseDir: "src/"
  projectKey: "my-custom-project"
```

### Inputs

These are some of the supported input parameters of action.

| **Parameter**        | **Description**                                   | **Required?** | **Default** | **Note**                                                                                      |
|----------------------|---------------------------------------------------|---------------|-------------|-----------------------------------------------------------------------------------------------|
| **`host`**           | SonarQube server URL                              | 🟢            |             |                                                                                               |
| **`login`**          | Login or authentication token of a SonarQube user | 🟢            |             | `Execute Analysis` permission required.                                                       |
| **`password`**       | The password that goes with the `login` username  | 🔴            |             | This should be left blank if an `login` are authentication token.                             |
| **`projectBaseDir`** | Set custom project base directory analysis        | 🔴            | `.`         |                                                                                               |
| **`projectKey`**     | The project's unique key                          | 🔴            |             | Allowed characters are: letters, numbers, `-`, `_`, `.` and `:`, with at least one non-digit. |
| **`projectName`**    | Name of the project                               | 🔴            |             | It will be displayed on the SonarQube web interface.                                          |
| **`projectVersion`** | The project version                               | 🔴            |             |                                                                                               |
| **`encoding`**       | Encoding of the source code                       | 🔴            | `UTF-8`     |                                                                                               |


> [!NOTE]
> If you opt to configure the project metadata and other related settings in a **`sonar-project.properties`** file (must be placed within the base directory, `projectBaseDir`) instead of using input parameters, this action is compatible with that approach!

# I'm are always open to your feedback.  Please contact as bellow information:
### [Contact ]
* [Name: nho Luong]
* [Skype](luongutnho_skype)
* [Github](https://github.com/nholuongut/)
* [Linkedin](https://www.linkedin.com/in/nholuong/)
* [Email Address](luongutnho@hotmail.com)

![](https://i.imgur.com/waxVImv.png)
![](bitfield.png)
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/nholuong)

# License
* Nho Luong (c). All Rights Reserved.