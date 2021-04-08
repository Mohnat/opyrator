<!-- markdownlint-disable MD033 MD041 -->
<h1 align="center">
    opyrator
</h1>

<p align="center">
    <strong>Python functions with superpowers. Instantly deploy with REST API, UI, and more.</strong>
</p>

<p align="center">
    <a href="https://github.com/ml-tooling/opyrator/blob/main/LICENSE" title="Project License"><img src="https://img.shields.io/badge/License-MIT-green.svg"></a>
    <a href="https://github.com/ml-tooling/opyrator/actions?query=workflow%3Abuild-pipeline" title="Build status"><img src="https://img.shields.io/github/workflow/status/ml-tooling/opyrator/build-pipeline?style=flat"></a>
    <a href="ttps://mltooling.substack.com/subscribe" title="Subscribe to newsletter"><img src="http://bit.ly/2Md9rxM"></a>
    <a href="https://twitter.com/mltooling" title="Follow on Twitter"><img src="https://img.shields.io/twitter/follow/mltooling.svg?style=social&label=Follow"></a>
</p>

<p align="center">
  <a href="#getting-started">Getting Started</a> •
  <a href="#features">Features & Screenshots</a> •
  <a href="#support--feedback">Support</a> •
  <a href="https://github.com/ml-tooling/opyrator/issues/new?labels=bug&template=01_bug-report.md">Report a Bug</a> •
  <a href="#contribution">Contribution</a> •
  <a href="https://github.com/ml-tooling/opyrator/releases">Changelog</a>
</p>

Opyrator enables you to instantly turn a simple Python function into a powerful web service that includes a REST API and a full-blown graphical UI. It can be saved & shared as self-contained executable file and instantly deployed & scaled for production usage. Opyrator is powered by Pydantic, FastAPI, and Streamlit and enables you to build your web apps and services within seconds.

## Highlights

- 🪄&nbsp; Turn functions into production-ready services within seconds.
- 🔌&nbsp; Auto-generated HTTP REST API based on FastAPI.
- 🌅&nbsp; Auto-generated Web UI based on Streamlit.
- 📦&nbsp; Save and share as self-contained executable file or Docker image.
- 🧩&nbsp; Reuse pre-defined interfaces & combine with existing Opyrators.
- 📈&nbsp; Instantly deploy and scale for production usage.

## Getting Started

### Installation

> _Requirements: Python 3.6+._

```bash
pip install opyrator
```

### Usage

1. A simple Opyrator-compatible function could look like this:

    ```python
    from pydantic import BaseModel
    import time

    def Input(BaseModel):
        text: str
        wait: int

    def Output(BaseModel):
        text: str

    def hello_world(input: Input) -> Output:
        time.sleep(input.wait)
        return Output(text=input.text)
    ```
    _Requirements: The function needs to be annotated with typing hints, and the `input` parameter and return value needs to be based on [Pydantic models](https://pydantic-docs.helpmanual.io/)._

2. Copy this code to a file `my_opyrator.py`
3. Run the UI server from command-line:

    ```bash
    opyrator launch-ui my_opyrator:hello_world
    ```
    _In the output, there's a line that shows where your web app is being served, on your local machine._

    TODO: Add screenshot

4. Run the REST API server from command-line:

    ```bash
    opyrator launch-api my_opyrator:hello_world
    ```
    _In the output, there's a line that shows where your web service is being served, on your local machine._

    TODO: Add screenshot
5. Find out more usage details and features in the [Features](#features) section.

## Support & Feedback

This project is maintained by [Benjamin Räthlein](https://twitter.com/raethlein), [Lukas Masuch](https://twitter.com/LukasMasuch), and [Jan Kalkan](https://www.linkedin.com/in/jan-kalkan-b5390284/). Please understand that we won't be able to provide individual support via email. We also believe that help is much more valuable if it's shared publicly so that more people can benefit from it.

| Type                     | Channel                                              |
| ------------------------ | ------------------------------------------------------ |
| 🚨&nbsp; **Bug Reports**       | <a href="https://github.com/ml-tooling/opyrator/issues?utf8=%E2%9C%93&q=is%3Aopen+is%3Aissue+label%3Abug+sort%3Areactions-%2B1-desc+" title="Open Bug Report"><img src="https://img.shields.io/github/issues/ml-tooling/opyrator/bug.svg?label=bug"></a>                                 |
| 🎁&nbsp; **Feature Requests**  | <a href="https://github.com/ml-tooling/opyrator/issues?q=is%3Aopen+is%3Aissue+label%3Afeature+sort%3Areactions-%2B1-desc" title="Open Feature Request"><img src="https://img.shields.io/github/issues/ml-tooling/opyrator/feature.svg?label=feature%20request"></a>                                 |
| 👩‍💻&nbsp; **Usage Questions**   |  <a href="https://github.com/ml-tooling/opyrator/issues?q=is%3Aopen+is%3Aissue+label%3Asupport+sort%3Areactions-%2B1-desc" title="Open Support Request"> <img src="https://img.shields.io/github/issues/ml-tooling/opyrator/support.svg?label=support%20request"></a> <a href="https://gitter.im/ml-tooling/community" title="Chat on Gitter"><img src="https://badges.gitter.im/ml-tooling/community.svg"></a> |
| 📢&nbsp; **Announcements** | <a href="https://gitter.im/ml-tooling/community" title="Chat on Gitter"><img src="https://badges.gitter.im/mml-tooling/community.svg"></a>  <a href="https://mltooling.substack.com/subscribe" title="Subscribe for updates"><img src="http://bit.ly/2Md9rxM"></a> <a href="https://twitter.com/mltooling" title="ML Tooling on Twitter"><img src="https://img.shields.io/twitter/follow/mltooling.svg?style=social&label=Follow"> |
| ❓&nbsp; **Other Requests** | <a href="mailto:team@ml-tooling.org" title="Email ML Tooling Team"><img src="https://img.shields.io/badge/email-ML Tooling-green?logo=mail.ru&logoColor=white"></a> |

## Features

<p align="center">
  <a href="#rest-api">REST API</a> •
  <a href="#graphical-ui">Graphical UI</a> •
  <a href="#command-line interface">CLI</a> •
  <a href="#zip-export">ZIP Export</a> •
  <a href="#docker-export">Docker Export</a> •
  <a href="#python-client">Python Client</a> •
  <a href="#pre-defined-interfaces">Pre-defined Interfaces</a> •
</p>

### REST API

With Opyrator, you can instantly launch a local HTTP (REST) API server for any compatible function (callable), e.g.:

```bash
opyrator launch-api my_opyrator:hello_world
```

This will launch a [FastAPI](https://fastapi.tiangolo.com/) server based on the [OpenAPI standard](https://swagger.io/specification) and with an automatic interactive documentation.

_TODO: Add Screenshot_

_💡 Make sure that all requirements of your script are installed in the active Python enviornment._

The port and host used by the API server can be provided via CLI arguments:

```bash
opyrator launch-api my_opyrator:hello_world --port 8080 --host "0.0.0.0"
```

The API server can also be started via the exported zip-file format (see [zip export section](#zip-export) below).

```bash
opyrator launch-api my-opyrator.zip
```

### Graphical UI

You can launch a graphical user interface - powered by  [Streamlit](https://streamlit.io/) - for your compatible function. The UI is auto-generated from the input- and output-schema of the given function.

```bash
opyrator launch-ui my_opyrator:hello_world
```

_TODO: Screenshot_

_💡 Make sure that all requirements of your script are installed in the active Python environment._

You can influence most aspects of the UI just by changing and improving the input- and output-schema of your function. Furthermore, it is also possible to define custom UIs for the function input and output. For more details, refer to the [input- and output-schema](#TODO) section.

The port and host used by the UI server can be provided via CLI arguments:

```bash
opyrator launch-ui my_opyrator:hello_world --port 8080 --host "0.0.0.0"
```

The UI server can also be started via the exported zip-file format (see [zip export section](#zip-export) below).

```bash
opyrator launch-ui my-opyrator.zip
```

In addition, the UI server can be started by using an already running Opyrator API endpoint:

```bash
opyrator launch-ui http://my-opyrator:8080 
```

Thereby, all Opyrator calls from the UI will be executed via the configured HTTP endpoint instead of the Python function running inside the UI server.

### Command-line Interface

An Opyrator can also be executed via command-line:

```bash
opyrator call my_opyrator:hello_world '{"text": "hello", "wait": 1}'
```

The CLI interface also works using the [zip export format](#zip-export):

```bash
opyrator call my-opyrator.zip '{"text": "hello", "wait": 1}'
```

Or, by using an already running Opyrator API endpoint:

```bash
opyrator call http://my-opyrator:8080 '{"text": "hello", "wait": 1}'
```

Thereby, the function call is executed by the Opyrator API server, instead of locally using the Python function.

### ZIP Export

### Docker Export

### Python Client

### Pre-defined Interfaces

- For common tasks.

## Documentation

### Input- and Output-Schema

## Contribution

- Pull requests are encouraged and always welcome. Read our [contribution guidelines](https://github.com/ml-tooling/opyrator/tree/main/CONTRIBUTING.md) and check out [help-wanted](https://github.com/ml-tooling/opyrator/issues?utf8=%E2%9C%93&q=is%3Aopen+is%3Aissue+label%3A"help+wanted"+sort%3Areactions-%2B1-desc+) issues.
- Submit Github issues for any [feature request and enhancement](https://github.com/ml-tooling/opyrator/issues/new?assignees=&labels=feature&template=02_feature-request.md&title=), [bugs](https://github.com/ml-tooling/opyrator/issues/new?assignees=&labels=bug&template=01_bug-report.md&title=), or [documentation](https://github.com/ml-tooling/opyrator/issues/new?assignees=&labels=documentation&template=03_documentation.md&title=) problems.
- By participating in this project, you agree to abide by its [Code of Conduct](https://github.com/ml-tooling/opyrator/blob/main/.github/CODE_OF_CONDUCT.md).
- The [development section](#development) below contains information on how to build and test the project after you have implemented some changes.

## Development

> _**Requirements**: [Docker](https://docs.docker.com/get-docker/) and [Act](https://github.com/nektos/act#installation) are required to be installed on your machine to execute the containerized build process._

To simplify the process of building this project from scratch, we provide build-scripts - based on [universal-build](https://github.com/ml-tooling/universal-build) - that run all necessary steps (build, check, test, and release) within a containerized environment. To build and test your changes, execute the following command in the project root folder:

```bash
act -b -j build
```

Refer to our [contribution guides](https://github.com/ml-tooling/opyrator/blob/main/CONTRIBUTING.md#development-instructions) for more detailed information on our build scripts and development process.

---

Licensed **MIT**. Created and maintained with ❤️&nbsp; by developers from Berlin.
