# Interacting with Ansible
{% for link, url in book.url_index %}{% if link == "Ansible"%}[{{link}}]({{url}}){% endif %}{% endfor %} is an automation language that focuses on being simple, agentless, and powerful. By using simply defined, YAML based playbooks, nearly any end user of an IT system can use Ansible to automate large, complex tasks in a repeatable, secure, and human-readable fashion.

In 2015, Ansible the company was acquired by Red Hat and has since become integrated with many of our other products including OpenShift, Red Hat CloudForms, and Red Hat Enterprise Linux.

For partners who are interested, there are generally 4 ways to interact with Ansible:

- Playbooks & Roles
- Inventories & Plugins
- Modules
- Ansible Tower & it's API

And generally, most partners will take a 3 stage approach to leveraging Ansible. That  usually maps to something like:

**Stage 1:** Focus on playbooks and roles to simplify deployment of one or multiple parts of your end deliverable

**Stage 2:** Creating dynamic inventories, plugins, or modules to enhance integration with your end deliverable

**Stage 3:** Implementing the advanced features of Ansible Tower for an enterprise-class experience. This may be mapping select functionalities in your deliverable to specific northbound or southbound APIs, or offering a custom view of Ansible Tower within your deliverable.

This documentation will focus on these 4 ways for a few types of partners including:
- Systems Integrators
- Consulting partners
- OEM & ISV partners

My hope is to also cover some more basic discussion points around automation, such as why it's important, best practices, and how to prepare your customers for the future of automation.
