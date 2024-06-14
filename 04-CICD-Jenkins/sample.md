- ansible.cng
    * ansible configuration file

    In simple terms, an Ansible configuration file (ansible.cfg) is like a control center for Ansible. It's a plain text file where you can set various options and configurations that affect how Ansible behaves when running playbooks and managing infrastructure.

    use ansible.cfg to specify options such as the location of inventory files, where to find roles, the default user to connect to hosts, and many others.

    [cnf](https://docs.ansible.com/ansible/latest/reference_appendices/config.html#ansible-configuration-settings-locations)

* ansible template
    - .j2 (jinja formate) extension

    **Ansible templates are indeed configuration files that can contain dynamic parameters, such as variables, which are replaced with actual values during playbook execution.**

    **Dynamic Parameters**: Templates can include placeholders or variables, denoted by double curly braces ({{ variable_name }}), which are replaced with actual values when the template is processed.

    Flexibility: Templates allow for flexibility in configuration management by enabling the reuse of configuration files across multiple hosts or environments with variations in parameters.

    [template](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/template_module.html)

* ansible handlers

    Ansible handlers are special tasks that are only executed when they are notified by other tasks in the playbook. They are commonly used to restart services or perform other actions that should only occur when specific changes have been made.

* Ansible Tags

     which helps to execute particular task in playbook , to avoid run entire playbook 

* Ansible Vault
    storage of secretes
    
* ssm parameter store

* Dynamic Inventory



***
## Practice
* Ansible configuration 
* Ansible jinja templates
* Ansible Tags
* Ansible Handlers


***
search for 

async keyword is an ansible task

