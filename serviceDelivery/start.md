# Where to Start Automating
I often get a similar sounding question from many Red Hat partners which is "Where do we start trying to help customers automate?"

Generally, my response is that for you to more meaningfully make an impact, you should already understand where to help your customer. Being able to discover, explore, and empathize with your customer will eventually make you a stronger partner so it's important to get some good practices for exploring under your belt.

Here are a few techniques and questions you can try:

		a. "What is the most time consuming process in your environment day to day"?

Whatever this process is, it should probably be the first place your start trying to automate because that is how we derive value from automation: by helping teams recover more time and reduce errors. If it's a large process, begin breaking it down into smaller, more manageable chunks.

		b. "Are you currently automating anything today? How are you achieving that?"
Often we see success in helping people take their existing scripts or automation code and coverting it to Ansible playbooks which can be read, written, and used by all people within an organization because they require no programming skillset.

Whatever responses you get from these two basic questions, it can be good to start with the {% for link, url in book.url_index %}{% if link == "5 Whys Exercise"%}[{{link}}]({{url}}){% endif %}{% endfor %} which originally was derived from the lean manufacturing world to understand the human reasons behind technical issues.

Beyond that, here are some common use cases we see for helping to get people started with automation.

### Basics
**Provisioning**

One of the simplest places to begin automating is at the start of a system’s lifecycle with provisioning.  Ansible has a large amount of modules already available to start provisioning directly against both public providers like:
* AWS
* Azure
* Google Cloud

Along with private providers including:
* VMware
* OpenStack
* Red Hat Virtualization

Here is a simple example for quickly provisioning 3 identical systems on AWS EC2:
```
	- name: Provision 3 identical systems in EC2
	  ec2:
    	key_name: ansible
    	instance_type: t2.micro
    	image: ami-123456
    	wait: yes
    	group: webserver
    	count: 3
    	vpc_subnet_id: subnet-29e63245
    	assign_public_ip: yes
```
More EC2 examples available on the {% for link, url in book.url_index %}{% if link == "EC2 Module Page"%}[{{link}}]({{url}}){% endif %}{% endfor %}, or check out the full
For bare-metal provisioning systems such as iPXE, Ansible playbooks can be run post provisioning through a few methods:
* Ansible Tower allows for {% for link, url in book.url_index %}{% if link == "provisioning callbacks"%}[{{link}}]({{url}}){% endif %}{% endfor %} which is a simply defined POST to the Tower API using a method like `curl`.
* If using Ansible core, `ansible-pull` can be used at the end of a kickstart file in the %post section to pull a job from source control

```Note: It's important to recognize that by using ansible-pull, this defeats the centralized, agentless approach that Ansible normally creates. Using ansible-pull post provisioning is generally not recommended. Ansible-pull also requires that any playbooks be stored in a source-controlled repository such as a git repo, but this is generally a good practice no matter what.```


**Configuration Management**

Being able to automate basic system configuration is where many people first start with automation. That's because configuration management is useful to not only those with new provisioning needs (greenfield deployments) but also those with a mix of existing and new deployments (brownfield) to ensure consistency across old and new systems.

Configuration management can be as simple or complex as is needed, but ideally should not require any manual intervention after defining the desired state. This may include things like:
* package versioning ( ex httpd )
* configuration files ( ex /etc/httpd/conf/httpd.conf)
* service state  ( systemctl enable httpd, systemctl start httpd)

If configuration files are kept in a source control system like a git repository, it becomes very easily to consistently configure systems. If you are able to build out config management processes into multiple roles, it can be easy to apply a basic set of configurations to all systems, and then role specific configurations for the specific duties of that system.

Some introductory Ansible playbooks to highlight configuration management can be found in the {% for link, url in book.url_index %}{% if link == "Ansible Examples Repo"%}[{{link}}]({{url}}){% endif %}{% endfor %}

**Application Deployment**

Using Ansible to deliver applications in a phased approach allows to customers to safely test and repeatably deploy their production workloads. There are several key characterists to Ansible, such as the `serial` or `delegate_to` options which make it easy to perform rolling updates, A/B or canary tests, and remove/reintroduce systems from clusters or load balancers as necessary.

For more on this topic, see {% for link, url in book.url_index %}{% if link == "Delegation, Rolling Updates, and Local Actions"%}[{{link}}]({{url}}){% endif %}{% endfor %}

### Speciality fields - Coming soon
<!-- **Infrastructure as Code**

**CICD**

**Networking** -->
