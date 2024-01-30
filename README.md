# Ansible Builder

This repository contains files and playbooks to automate the creation of execution environments (EEs) using Ansible Automation Controller. The main playbook `build_execution_environment.yml` is responsible for creating the EE. Reference the `infra.ee_utilities` collcetion in the Red Hat COP for more info. <https://github.com/redhat-cop/ee_utilities/tree/3.1.2/roles/ee_builder>

## Prerequisites
Before using this repository, ensure that the following requirements are met:
- Ansible Automation Controller is set up and configured.
- Access to the supported [job template](https://automation.uscis.dhs.gov/#/templates/job_template/414/details) or your own job template, with a survey that prompts for the `__build` variable

## Usage

1. Log into Ansible Automation Controller.
2. Navigate to the desired job template and launch it.
3. In the survey section, select the value for the `__build` variable.
4. Proceed with launching the job.

## File Descriptions

- `build_execution_environment.yml`: The main playbook responsible for creating the custom EE.

- `vars/common.yml`: Configuration file containing variables used in all execution environments. Modify this file to customize the environment settings.

- `vars/{{ __build }}.yml`: Example file specifying the files, certificates, and dependencies required for the custom EE. Modify this file according to your specific needs.

- `files/{{ __build}}/*`: Files folder for any additional files that need to be added to the execution environment. Note, you will also need to add the `build_items` and `build_files` variables to your `vars/{{ __build }}` file

## Contributing
If you or your team has any ee requirements, please open a pull request with your proposed changes that includes a link to your test job run.
