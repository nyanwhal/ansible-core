![Logo of the project](/docs/images/logo.png)

# Ansible Core
> A best practices compliant Ansible execution directory

After installing Ansible you can clone this repository to your Ansible host
and run local.yml to pull additional "core" Ansible content into a consistent 
Ansible environment. 

### What is an Ansible core resource?

To be included as "core" a source of Ansible content must meet the following criteria:

- Is useful in all or nearly all installation scenarios
- Is composed of content from trusted sources
- Has been submitted for peer review and approved
- Has been thoroughly tested against all appropriate target hosts

### What about Ansible content that doesn't meet core criteria?

All approved Ansible content will need to meet three of those criteria:

- Is composed of content from trusted sources
- Has been submitted for peer review and approved
- Has been thoroughly tested against all appropriate target hosts

Not all content is included in core because not all content is appropriate for every installation.

To incorporate content suited for more specialized tasks or contexts see the "Building" section below.


## Installing / Getting started

Install Ansible on your target host. (See "Prerequisites" section below.)

Clone this repository to your Ansible host.

```shell
git clone https://github.com/nyanwhal/ansible-core.git
```

Running local.yml will pull the repositories listed in import/sources.yml and 
execute the role "core/main" to configure the Ansible instance and provide 
access to additional "core" repositories and resources. 

```shell
cd ansible-core
ansible-playbook -v local.yml
```

The verbose argument above "-v" is stackable to increase output verbosity
for the curious.

```shell
ansible-playbook -vvvv local.yml
```


### Built With

- ansible 2.9.2
- python version = 3.7.6 (default, Dec 27 2019, 09:51:21) [Clang 11.0.0 (clang-1100.0.33.16)]


### Prerequisites

You will need to install Ansible on a target host.

Installing Ansible on 
[Linux](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html "Linux") or 
[OS X](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#latest-releases-via-pip "OS X") via pip.
For Windows hosts running WSL see [this discussion](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html "Windows").


### Setting up Dev

See the "Getting started" and "Prerequesites" sections above.

Note: This repository is NOT intended for developing playbooks, roles etc.

Please use the appropriate repos for those types of content ie. 
- /ansible-core-roles 
- /ansible-core-playbooks
etc.

For content suited for more specialized tasks or contexts there are additional 
repositories and more can be created.


### Building

To modify sources for an Ansible instance you can edit /import/sources.yml

sources.yml is not tracked in version control (.gitignore) to allow clean local 
modification at the instance level 

You can also run local.yml with the source_file argument to pull Ansible content from 
arbitrary sources listed in an alternate file.

```shell
ansible-playbook -v local.yml --extra-vars "source_file=foo.yml"
```

local.yml expects a role in roles/core called main to hand off further setup.
See that role for details about instance configuration and adding additional resources 
like Galaxy content.


### Deploying / Publishing

Before making a pull request to merge your changes do the following

- Test your branch on a compliant Ansible server against all appropriate target hosts

- Make sure you're not tracking content in any of the following directories:
> import, playbooks, roles

- If you want to contribute global changes to individual files not being tracked remotely 
(ansible.cfg, .editorconfig, sources.yml etc) 
make sure to discuss with peers and use force add.

```shell
git add -f file_you_are_sure_you_want_to_commit
```


## Configuration

Configuration is handled by running the local.yml playbook.

See the "Building" section above for details. 


## Tests

See the official Ansible documentation on testing strategies
https://docs.ansible.com/ansible/latest/reference_appendices/test_strategies.html

See [this blog post](https://www.jeffgeerling.com/blog/2018/testing-your-ansible-roles-molecule)
by an established contributor of Ansible Galaxy content, about molecule for testing roles.


## Style guide

The [Ansible style guide](https://github.com/nyanwhal/guidelines/ansible) is maintained in Github 
with additional guidelines here in [docs/styleguide.md](./docs/styleguide.md).

