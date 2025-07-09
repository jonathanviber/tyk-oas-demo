<<<<<<< HEAD
<<<<<<< HEAD
# Tyk OAS Demo

> **⚠️ CONTRIBUTIONS WELCOME!** This implementation has some [known issues](#known-issues) and missing features. Pull requests are welcome to improve, fix, or enhance this demo!

A production-ready Tyk OSS API Gateway implementation using OpenAPI Specification (OAS) for GitOps-style endpoint management.

## Overview

This demo showcases a typical production Tyk setup with:
- **Performance optimizations** for high-scale deployments
- **GitOps approach** with OAS specifications stored in the repository
- **Logging** via Redis for collection by Tyk Pump
- **Metrics collection** using OpenTelemetry with Prometheus endpoints
- **Circuit breaker** all endpoints should implement a circuit breaker
- **Caching** Most GET endpoints should cache in REDIS
- **Rate Limiting** Some endpoints should use rate limiting with REDIS as the storage.
- **JWT Auth** Authenticating a JWT by using a JWKS 
- **Request Validation** validating of headers, query strings, payload etc. based on the OAS schema
- **HTTP/2** Requests form the client to TYK and requests from TYK to the upstream should be HTTP/2


## Quick Start

```bash
docker compose up
```

## Endpoints

### Upstream APIs (Direct Access)
- **HTTPBin**: http://localhost/
- **Echo Server**: http://localhost:81

### Tyk Gateway
- **WORKING API Endpoints**: http://localhost:8080/api/get | http://localhost:8080/api/uuid
- **NOT WORKING API Endpoints**: http://localhost:8080/api/echo

### Admin & Monitoring
- **Health Check**: http://localhost:5555/health
- **Metrics**: http://localhost:5555/metrics

## Architecture

- **Gateway**: Tyk OSS Gateway with production-ready configuration
- **Storage**: Redis for caching, rate-limiting and log aggregation
- **Monitoring**: OTEL metrics exported to Prometheus format
- **Logging**: Structured logs sent to Redis (Tyk Pump not included)
- **Configuration**: OAS-based API definitions for GitOps workflows

## Known Issues
- **OAS Config not working**: I have a file called api-config.json which I believe should not be necessary but if I remove it, my APIs don't register
- **Echo Endpoints**: The downstream server http://echo is configured in echo-api.json but it is calling the proxy in api-config.json
- **Metrics endpoint**: http://localhost:5555/metrics is not working correctly
- **HTTP/2 not working**: Calling endpoints from Insomnia show that they are using HTTP/1.1

## Not Yet Added
- **Caching**
- **Rate limiting**
- **Circuit breaker**
- **Logging**
- **Performance Optimizations**
- **Payload validation**
- **CORS settings**
- **JWT Authentication**
- **Request Validation**
=======
=======
>>>>>>> 105e276 (update)
# Tyk POC



## Getting started

To make it easy for you to get started with GitLab, here's a list of recommended next steps.

Already a pro? Just edit this README.md and make it your own. Want to make it easy? [Use the template at the bottom](#editing-this-readme)!

## Add your files

- [ ] [Create](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#create-a-file) or [upload](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#upload-a-file) files
- [ ] [Add files using the command line](https://docs.gitlab.com/ee/gitlab-basics/add-file.html#add-a-file-using-the-command-line) or push an existing Git repository with the following command:

```
cd existing_repo
git remote add origin https://lab.vibelab.net/units/dotco/architects/api-gw/tyk-poc.git
git branch -M main
git push -uf origin main
```

## Integrate with your tools

- [ ] [Set up project integrations](https://lab.vibelab.net/units/dotco/architects/api-gw/tyk-poc/-/settings/integrations)

## Collaborate with your team

- [ ] [Invite team members and collaborators](https://docs.gitlab.com/ee/user/project/members/)
- [ ] [Create a new merge request](https://docs.gitlab.com/ee/user/project/merge_requests/creating_merge_requests.html)
- [ ] [Automatically close issues from merge requests](https://docs.gitlab.com/ee/user/project/issues/managing_issues.html#closing-issues-automatically)
- [ ] [Enable merge request approvals](https://docs.gitlab.com/ee/user/project/merge_requests/approvals/)
- [ ] [Set auto-merge](https://docs.gitlab.com/ee/user/project/merge_requests/merge_when_pipeline_succeeds.html)

## Test and Deploy

Use the built-in continuous integration in GitLab.

- [ ] [Get started with GitLab CI/CD](https://docs.gitlab.com/ee/ci/quick_start/index.html)
- [ ] [Analyze your code for known vulnerabilities with Static Application Security Testing (SAST)](https://docs.gitlab.com/ee/user/application_security/sast/)
- [ ] [Deploy to Kubernetes, Amazon EC2, or Amazon ECS using Auto Deploy](https://docs.gitlab.com/ee/topics/autodevops/requirements.html)
- [ ] [Use pull-based deployments for improved Kubernetes management](https://docs.gitlab.com/ee/user/clusters/agent/)
- [ ] [Set up protected environments](https://docs.gitlab.com/ee/ci/environments/protected_environments.html)

***

# Editing this README

When you're ready to make this README your own, just edit this file and use the handy template below (or feel free to structure it however you want - this is just a starting point!). Thanks to [makeareadme.com](https://www.makeareadme.com/) for this template.

## Suggestions for a good README

Every project is different, so consider which of these sections apply to yours. The sections used in the template are suggestions for most open source projects. Also keep in mind that while a README can be too long and detailed, too long is better than too short. If you think your README is too long, consider utilizing another form of documentation rather than cutting out information.

## Name
Choose a self-explaining name for your project.

## Description
Let people know what your project can do specifically. Provide context and add a link to any reference visitors might be unfamiliar with. A list of Features or a Background subsection can also be added here. If there are alternatives to your project, this is a good place to list differentiating factors.

## Badges
On some READMEs, you may see small images that convey metadata, such as whether or not all the tests are passing for the project. You can use Shields to add some to your README. Many services also have instructions for adding a badge.

## Visuals
Depending on what you are making, it can be a good idea to include screenshots or even a video (you'll frequently see GIFs rather than actual videos). Tools like ttygif can help, but check out Asciinema for a more sophisticated method.

## Installation
Within a particular ecosystem, there may be a common way of installing things, such as using Yarn, NuGet, or Homebrew. However, consider the possibility that whoever is reading your README is a novice and would like more guidance. Listing specific steps helps remove ambiguity and gets people to using your project as quickly as possible. If it only runs in a specific context like a particular programming language version or operating system or has dependencies that have to be installed manually, also add a Requirements subsection.

## Usage
Use examples liberally, and show the expected output if you can. It's helpful to have inline the smallest example of usage that you can demonstrate, while providing links to more sophisticated examples if they are too long to reasonably include in the README.

## Support
Tell people where they can go to for help. It can be any combination of an issue tracker, a chat room, an email address, etc.

## Roadmap
If you have ideas for releases in the future, it is a good idea to list them in the README.

## Contributing
State if you are open to contributions and what your requirements are for accepting them.

For people who want to make changes to your project, it's helpful to have some documentation on how to get started. Perhaps there is a script that they should run or some environment variables that they need to set. Make these steps explicit. These instructions could also be useful to your future self.

You can also document commands to lint the code or run tests. These steps help to ensure high code quality and reduce the likelihood that the changes inadvertently break something. Having instructions for running tests is especially helpful if it requires external setup, such as starting a Selenium server for testing in a browser.

## Authors and acknowledgment
Show your appreciation to those who have contributed to the project.

## License
For open source projects, say how it is licensed.

## Project status
If you have run out of energy or time for your project, put a note at the top of the README saying that development has slowed down or stopped completely. Someone may choose to fork your project or volunteer to step in as a maintainer or owner, allowing your project to keep going. You can also make an explicit request for maintainers.
<<<<<<< HEAD
>>>>>>> ae08762 (Initial commit)
=======
=======
# Tyk OAS Demo

> **⚠️ CONTRIBUTIONS WELCOME!** This implementation has some [known issues](#known-issues) and missing features. Pull requests are welcome to improve, fix, or enhance this demo!

A production-ready Tyk OSS API Gateway implementation using OpenAPI Specification (OAS) for GitOps-style endpoint management.

## Overview

This demo showcases a typical production Tyk setup with:
- **Performance optimizations** for high-scale deployments
- **GitOps approach** with OAS specifications stored in the repository
- **Logging** via Redis for collection by Tyk Pump
- **Metrics collection** using OpenTelemetry with Prometheus endpoints
- **Circuit breaker** all endpoints should implement a circuit breaker
- **Caching** Most GET endpoints should cache in REDIS
- **Rate Limiting** Some endpoints should use rate limiting with REDIS as the storage.
- **JWT Auth** Authenticating a JWT by using a JWKS 
- **Request Validation** validating of headers, query strings, payload etc. based on the OAS schema
- **HTTP/2** Requests form the client to TYK and requests from TYK to the upstream should be HTTP/2


## Quick Start

```bash
docker compose up
```

## Endpoints

### Upstream APIs (Direct Access)
- **HTTPBin**: http://localhost/
- **Echo Server**: http://localhost:81

### Tyk Gateway
- **WORKING API Endpoints**: http://localhost:8080/api/get | http://localhost:8080/api/uuid
- **NOT WORKING API Endpoints**: http://localhost:8080/api/echo

### Admin & Monitoring
- **Health Check**: http://localhost:5555/health
- **Metrics**: http://localhost:5555/metrics

## Architecture

- **Gateway**: Tyk OSS Gateway with production-ready configuration
- **Storage**: Redis for caching, rate-limiting and log aggregation
- **Monitoring**: OTEL metrics exported to Prometheus format
- **Logging**: Structured logs sent to Redis (Tyk Pump not included)
- **Configuration**: OAS-based API definitions for GitOps workflows

## Known Issues
- **OAS Config not working**: I have a file called api-config.json which I believe should not be necessary but if I remove it, my APIs don't register
- **Echo Endpoints**: The downstream server http://echo is configured in echo-api.json but it is calling the proxy in api-config.json
- **Metrics endpoint**: http://localhost:5555/metrics is not working correctly
- **HTTP/2 not working**: Calling endpoints from Insomnia show that they are using HTTP/1.1

<<<<<<< HEAD
- **Metrics endpoint**: http://localhost:5555/metrics is not working correctly
>>>>>>> 0c05fa9 (initial commit)
=======
## Not Yet Added
- **Caching**
- **Rate limiting**
- **Circuit breaker**
<<<<<<< HEAD
- **Logging** 
>>>>>>> fd306ad (Split APIs to separate files, enable HTTP/2)
=======
- **Logging**
- **Performance Optimizations**
- **Payload validation**
- **CORS settings**
- **JWT Authentication**
- **Request Validation**
>>>>>>> a52ac9e (add to readme)
>>>>>>> 105e276 (update)
