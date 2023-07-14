# ansible_builder

This repository contains files and playbooks to automate the creation of a custom execution environment (EE) using Ansible Automation Controller. The main playbook `build.yml` is responsible for creating the custom EE.

## Prerequisites
Before using this repository, ensure that the following requirements are met:
- Ansible Automation Controller is set up and configured.
- A job template is created with a survey question that prompts for the `__build` variable. In this repo `cisco` would be the answer to the survey options.
- The execution environment running the job inherits the necessary certificates from controller.

## Usage

1. Log into Ansible Automation Controller.
2. Navigate to the desired job template and launch it.
3. In the survey section, select `cisco` as the value for the `__build` parameter.
4. Proceed with launching the job.

## File Descriptions

- `build.yml`: The main playbook responsible for creating the custom EE. It includes the necessary roles and performs pre-tasks as a workaround for version 2.0.8 of the `ee_utilities` role. Note that the latest version of the role has a built-in method for including the necessary files.
  - The pre-tasks in this playbook create the path for the builder and copy extra files to the workstation if the `builder_dir` variable is defined.
  - The certificates are copied from the execution environment running the job, as `/etc/pki/ca-trust` is exposed in the controller job settings.

- `common.yml`: Configuration file containing variables used in the playbook. Modify this file to customize the environment settings.

- `cisco.yml`: Example file specifying the files, certificates, and dependencies required for the custom EE. Modify this file according to your specific needs.

Feel free to explore the repository and adapt it to your requirements. If you have any questions reach out.
