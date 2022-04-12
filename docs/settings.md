<!-- {{! Do not edit this file directly. This is generated by the `generate-settings-readme` npm script }} -->

# Language Server Settings

The following are the default values of the settings provided by the Ansible Language Server:

- **ansible.ansible.path**:
Path to the ansible executable \
_default value:
`ansible`_

- **ansible.ansible.useFullyQualifiedCollectionNames**:
Toggle usage of fully qualified collection names (FQCN) when inserting module names \
_default value:
`true`_

- **ansible.ansibleLint.enabled**:
Toggle usage of ansible-lint \
_default value:
`true`_

- **ansible.ansibleLint.path**:
Path to the ansible-lint executable \
_default value:
`ansible-lint`_

- **ansible.ansibleLint.arguments**:
Optional command line arguments to be appended to ansible-lint invocation \
_default value:
`""`_

- **ansible.python.interpreterPath**:
Path to the python/python3 executable. This settings may be used to make the extension work with ansible and ansible-lint installations in a python virtual environment \
_default value:
`""`_

- **ansible.python.activationScript**:
Path to a custom activation script, which is to be used instead of te settings above to run in a python virtual environment \
_default value:
`""`_

- **ansible.executionEnvironment.containerEngine**:
Container engine to be used while running with execution environment. valid values are &#x27;auto&#x27;, &#x27;podman&#x27; and &#x27;docker&#x27;. For &#x27;auto&#x27;, it will look for &#x27;podman&#x27; and then for &#x27;docker&#x27; \
_default value:
`auto`_

- **ansible.executionEnvironment.enabled**:
Toggle usage of an execution environment \
_default value:
`false`_

- **ansible.executionEnvironment.image**:
Name of the execution environment to be used \
_default value:
`quay.io/ansible/creator-ee:latest`_

- **ansible.executionEnvironment.pullPolicy**:
Image pull policy to be used. Valid values are &#x27;always&#x27;, &#x27;missing&#x27;, &#x27;never&#x27; and &#x27;tag&#x27;. always will always pull the image when extension is activated or reloaded. &#x27;missing&#x27; will pull if not locally available. &#x27;never&#x27; will never pull the image and &#x27;tag&#x27; will always pull if the image tag is &#x27;latest&#x27;, otherwise pull if not locally available. \
_default value:
`missing`_
