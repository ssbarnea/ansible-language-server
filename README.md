# Ansible Language Server

[//]: # DO-NOT-REMOVE-README-TITLE

This language server adds support for Ansible and is currently used by the
following projects:

- [Ansible extension for vscode/codium](https://github.com/ansible/vscode-ansible)
- [Ansible extension for coc.nvim](https://github.com/yaegassy/coc-ansible)

## Features

### Syntax highlighting

![Syntax highlighting](https://github.com/ansible/ansible-language-server/raw/main/images/syntax-highlighting.png)

**Ansible keywords**, **module names** and **module options**, as well as
standard YAML elements are recognized and highlighted distinctly. Jinja
expressions are supported too, also those in Ansible conditionals (`when`,
`failed_when`, `changed_when`, `check_mode`), which are not placed in double
curly braces.

> The screenshots and animations presented in this README have been taken using
> the One Dark Pro theme. The default VS Code theme will not show the syntax
> elements as distinctly unless customized. Virtually any theme other than
> default will do better.

### Validation

![YAML validation](https://github.com/ansible/ansible-language-server/raw/main/images/yaml-validation.gif)

While you type, the syntax of your Ansible scripts is verified and any feedback
is provided instantaneously.

#### Integration with ansible-lint

![Linter support](https://github.com/ansible/ansible-language-server/raw/main/images/ansible-lint.gif)

On opening and saving a document, `ansible-lint` is executed in the background
and any findings are presented as errors. You might find it useful that
rules/tags added to `warn_list` (see
[Ansible Lint Documentation](https://ansible-lint.readthedocs.io/en/latest/configuring.html))
are shown as warnings instead.

> If you also install `yamllint`, `ansible-lint` will detect it and incorporate
> into the linting process. Any findings reported by `yamllint` will be exposed
> in VSCode as errors/warnings.

**_Note_**

If `ansible-lint` is not installed/found or running `ansible-lint` results in
error it will fallback to `ansible --syntax-check` for validation.

### Smart auto-completion

![Autocompletion](https://github.com/ansible/ansible-language-server/raw/main/images/smart-completions.gif)

The extension tries to detect whether the cursor is on a play, block or task
etc. and provides suggestions accordingly. There are also a few other rules that
improve user experience:

- the `name` property is always suggested first
- on module options, the required properties are shown first, and aliases are
  shown last, otherwise ordering from the documentation is preserved
- FQCNs (fully qualified collection names) are inserted only when necessary;
  collections configured with the [`collections` keyword] are honored. This
  behavior can be disabled in extension settings.

[`collections` keyword]:
  https://docs.ansible.com/ansible/latest/user_guide/collections_using.html#simplifying-module-names-with-the-collections-keyword

#### Auto-closing Jinja expressions

![Easier Jinja expression typing](https://github.com/ansible/ansible-language-server/raw/main/images/jinja-expression.gif)

When writing a Jinja expression, you only need to type `"{{<space>`, and it will
be mirrored behind the cursor (including the space). You can also select the
whole expression and press `space` to put spaces on both sides of the
expression.

### Documentation reference

![Documentation on hover](https://github.com/ansible/ansible-language-server/raw/main/images/hover-documentation-module.png)

Documentation is available on hover for Ansible keywords, modules and module
options. The extension works on the same principle as `ansible-doc`, providing
the documentation straight from the Python implementation of the modules.

#### Jump to module code

![Go to code on Ctrl+click](https://github.com/ansible/ansible-language-server/raw/main/images/go-to-definition.gif)

You may also open the implementation of any module using the standard _Go to
Definition_ operation, for instance, by clicking on the module name while
holding `ctrl`/`cmd`.

## Language Server Settings

The following settings are supported.

- `ansible.ansible.path`: Path to the `ansible` executable. Default is
  `ansible`, which means $PATH is searched for the executable.
- `ansible.ansible.useFullyQualifiedCollectionNames`: Toggles use of fully
  qualified collection names (FQCN) when inserting a module name. Disabling it
  will only use FQCNs when necessary, that is when the collection is not
  configured for the task. Default is `true`.
- `ansible.ansibleLint.arguments`: Optional command line arguments to be
  appended to `ansible-lint` invocation. See `ansible-lint` documentation.
  Default is empty string.
- `ansible.ansibleLint.enabled`: Enables/disables use of `ansible-lint`. default
  is `true`.
- `ansible.ansibleLint.path`: Path to the `ansible-lint` executable. Default is
  `ansible-lint`, which means $PATH is searched for the executable.
- `ansible.ansibleNavigator.path`: Path to the `ansible-navigator` executable.
- `ansible.ansiblePlaybook.path`: Path to the `ansible-playbook` executable.
- `ansible.executionEnvironment.containerEngine`: The container engine to be
  used while running with execution environment. Valid values are `auto`,
  `podman` and `docker`. For `auto` it will look for `podman` then `docker`.
  Default is `auto`.
- `ansible.executionEnvironment.enabled`: Enable or disable the use of an
  execution environment. Default is `false`.
- `ansible.executionEnvironment.image`: Specify the name of the execution
  environment image. Default is `quay.io/ansible/creator-ee:latest`.
- `ansible.executionEnvironment.pullPolicy`: Specify the image pull policy.
  Valid values are `always`, `missing`, `never` and `tag`. Setting `always` will
  always pull the image when extension is activated or reloaded. Default is
  `missing`. Setting `missing` will pull if not locally available. Setting
  `never` will never pull the image and setting tag will always pull if the
  image tag is 'latest', otherwise pull if not locally available.
- `ansible.python.interpreterPath`: Path to the `python`/`python3` executable.
  This setting may be used to make the extension work with `ansible` and
  `ansible-lint` installations in a Python virtual environment. Default is empty
  string.
- `ansible.python.activationScript`: Path to a custom `activate` script, which
  will be used instead of the setting above to run in a Python virtual
  environment. Default is empty string.

## Developer support

For details on setting up development environment and debugging refer to the
[development document].

[development document]:
  https://github.com/ansible/ansible-language-server/blob/main/docs/development.md

## Requirements

- [Ansible 2.9+](https://docs.ansible.com/ansible/latest/index.html)
- [Ansible Lint](https://ansible-lint.readthedocs.io/en/latest/) (required,
  unless you disable linter support)
- [yamllint](https://yamllint.readthedocs.io/en/stable/) (optional)

For Windows users, this extension works perfectly well with extensions such as
`Remote - WSL` and `Remote - Containers`.

> If you have any other extension providing language support for Ansible, you
> might need to uninstall it first.

## Known limitations

- The shorthand syntax for module options (key=value pairs) is not supported.
- Only Jinja _expressions_ inside Ansible YAML files are supported. In order to
  have syntax highlighting of Jinja template files, you'll need to install other
  extension.
- Jinja _blocks_ (inside Ansible YAML files) are not supported yet.

## Credit

Based on the good work done by
[Tomasz Maciążek](https://github.com/tomaciazek/vscode-ansible)
