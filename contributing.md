Contributions are certainly welcome.

Development process:
If you would like to contribute to content,typos,errors that you find please feel free to use the branch content_drafts or create your own specific branch that identifies the enhancement.

If you'd like to contribute to the overall structure, such as table of contents, or net-new suggested topics, please use the structure branch.

This repo is served as a book via gitbooks.com -- which offers local testing suites including a live-reload on saves. It is built on top of NodeJS's Express framework, and further details on installing the framework for local development can be found here:
at their documentation site, https://toolchain.gitbook.com/setup.html

Links:
If you'd like to provide a link I do politely insist that you add it as an item to the JSON url_index dictionary within book.json
From there, any time you link within a document please do so using the format within the raw tags below:
{% raw %}{% for link, url in book.url_index %}{% if link == "Ansible"%}{{link}}{% endif %}{% endfor %}{% endraw %}

Why is that?
In short, rather than worry about links being broken or outdated, adding them to the book.json url_index dictionary today will allow for automated testing of URLs in the future. By adding them there and formatting the links as listed above, you'll be ensuring the stability of the project in the long term. That's pretty cool right?

Tests:
Today, anything with a pull request submitted against master will go through a default test in Travis CI to ensure that there are no templating errors that would cause a build failure on the book.

In the future, automated testing of URLs within the file book.json's url_index dictionary will be tested against the appendix.md document

Questions? Feel free to open and issue and let me know!
