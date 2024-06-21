# Splunk Forwarder Ansible Role

This Ansible role installs, updates, and manages the Splunk Universal Forwarder on Linux and Windows servers. The role ensures that the specified version of the Splunk Forwarder is installed and running.

## Requirements

- Ansible 2.9 or higher
- Python 3.6 or higher
- AWX or Ansible Tower (for UI-based execution)
- Virtualenv for Python environment isolation (recommended)

## Role Variables

The following variables can be configured in the `defaults/main.yml` file:

```yaml
splunk_forwarder_state: present
splunk_version: "{{ default }}"
splunk_package_url: "https://download.splunk.com/products/universalforwarder/releases/{{ splunk_version }}/linux/splunkforwarder-{{ splunk_version }}-linux-2.6-x86_64.rpm"
splunk_package_windows_url: "https://download.splunk.com/products/universalforwarder/releases/{{ splunk_version }}/windows/splunkforwarder-{{ splunk_version }}-x64-release.msi"
custom_param: default_value


## **Folder Structure**


├── playbook.yml
├── roles
│   └── splunk_forwarder
│       ├── defaults
│       │   └── main.yml
│       ├── handlers
│       │   └── main.yml
│       ├── tasks
│       │   ├── check_splunk_version.yml
│       │   ├── detect_os.yml
│       │   ├── install_splunk.yml
│       │   ├── main.yml
│       │   ├── remove_splunk.yml
│       │   └── update_splunk.yml
│       └── README.md


## To run the playbook, use the following command, replacing the placeholder values with actual ones as needed
ansible-playbook -i inventory playbook.yml --extra-vars "default=<your_splunk_version> restapi_value=<your_custom_value>"


## Running in AWX or Ansible Tower
When using AWX or Ansible Tower, follow these steps:

Import the Playbook:

Upload the playbook and roles to AWX or Ansible Tower.
Create an Inventory:

Define your target hosts in the inventory.
Create a Job Template:

Link the playbook to a job template.
Define default and restapi_value as extra variables in the job template.
Launch the Job:

Run the job template, providing the required variables.

