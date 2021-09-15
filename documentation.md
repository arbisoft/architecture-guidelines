# Documentation

### On Boarding Document

An onboarding document should be created that gives an in detail view of the whole project. That includes

- Introduction of the project
- Technology stack of the project
- Different components of the project
- Engineering practices being used
- Link to setup guides
- Development workflow
- Project management tools/methodology being used

A good example of how an onboarding document should look like is:

[https://github.com/artsy/README/tree/master/onboarding](https://github.com/artsy/README/tree/master/onboarding)

### Setup Guide

Each repository must have a setup guide, that basically contains the steps in detail to have the project running locally.

Few guidelines to write a good setup guide are

- Setup guide should be written down considering a fresh OS, so make sure to include the OS level installations too in the documentation
- Consider that the person using the setup guide has no prior knowledge about the project, and he/she should be able to setup the project without requiring any help
- Add a section of _&quot;FAQ&quot;._ This should include the issues and their solutions that developers come across while setting up the project
- Once the document is complete, ask the QA engineer or request someone from another team, to setup the project using these guidelines. If they still face any issue while setup, that means the guidelines are not complete
- Make sure that the setup guide is updated as the project progresses

Docker is now-a-days is trending very rapidly. So if possible, try to setup your project through [docker](https://www.docker.com/) and [docker-compose](https://docs.docker.com/compose/). Through Docker, project can be set up using only a couple of commands and removes the errors that occur due to OS and machine differences.

### Readme

A README is a text file that introduces and explains a project. It contains information that is commonly required to understand what the project is about.

There are different templates available that can be used to write a good readme file.
For example:

[https://gist.github.com/PurpleBooth/109311bb0361f32d87a2](https://gist.github.com/PurpleBooth/109311bb0361f32d87a2)

Like other documents, we must make sure that readme file is up to date with the progress. Ideally, it should be part of the issues/stories of the project that the related documents should be updated.