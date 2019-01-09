# Saltmaster Image

This repo is for the saltmaster image that is used by the dev services team for the salt-ssh docker container image. This will run in a continous integration server that is used for building this image.


## Pipeline Architecture

1. This will build the image that we use for the salt-stack provision repo.
2. On a pull request the following will happen, it will create a container.
  1. The container will be built
  2. Unit tests will run against it to make sure that it is good
  3. The image will not be pushed to the container registry
3. On merge into master from the branch it will do the following
  1. The container will be built
  2. Unit tests will run against it to make sure that it is a quality build
  3. The tag will be pushed to the git repo
  4. The image will be tagged as salt-ssh:<tag>
  5. The build will also replace the latest tag

## Getting Started

1. Clone the repo using git, 

```
  git clone https://tfs.assurant.com:8080/tfs/GH-Encore/ASP.Encore-SSP/_git/SSP-SRE-FileStash
```




### Prerequisites

Installable pre-requisites can be done through the `.local` directory. 


## Contributing

Anybody can contribute to this repo, however they have to go through the correct process. The process is very simple.

1. Clone the current repo
2. Create a feature branch in the following format ${TICKET-NUMBER}-${Hyphenated-title-of-task-or-bug}
  a. for example your bug could be named 1234 Add salt stack to dev tools it would look like this `1234-add-salt-stack-to-dev-tools`
3. Create a pull request inside TFS and assign it to another developer to do a code review
  a. The first process a code review goes through is an automated unit test and a linting process, if this fails the PR is failed
4. After other developer does code review click on that `Accept` Button. 
5. If the code review does not follow our standards for style or the pull request adds no value, work with the developer and explain why we are rejecting the Pull Request or allow them to fix and amend the request for submission


## Changelog
* [301462](https://tfs.assurant.com:8080/tfs/GH-Encore/ASP.Encore-SSP/_workitems/edit/301462) - Deploy salt master using saltify


## Built With

* [Markdown](https://en.wikipedia.org/wiki/Markdown) - The langua franca of developer docs
* [Scoop](https://scoop.sh/) - A **Better** package manager for windows
* [Salt](https://saltstack.com) - A CM tool for multi envirionments


## Authors

* **Michael Thomas Roth** - *Initial work* 