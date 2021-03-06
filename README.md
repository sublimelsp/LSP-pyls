# LSP-pyls

This is a helper package that automatically installs and updates the
[Python Language Server](https://github.com/palantir/python-language-server) (pyls) for you.

To use this package, you must have:

- An executable `python` (on Windows) or `python3` (on Linux/macOS)
- The [LSP](https://packagecontrol.io/packages/LSP) package
- For Ubuntu and Debian users, you must also install `python3-venv` with `apt`

## Applicable Selectors

This language server operates on views with the `source.python` base scope.

## Installation Location

The server is installed in the `$DATA/Cache/LSP-pyls` directory, where `$DATA` is the base data path of Sublime Text.
For instance, `$DATA` is `~/.config/sublime-text` on a Linux system. If you want to force a re-installation of the server,
you can delete the entire `$DATA/Cache/LSP-pyls` directory. The installation is done through a virtual environment, using
pip. Therefore, you must have at least the `python` executable installed and it must be present in your `$PATH`.

Like any helper package, installation starts when you open a view that is suitable for this language server. In this
case, that means that when you open a view with the `source.python` base scope, installation commences.

## Configuration

Configure the Python Language Server by accessing `Preferences > Package Settings > LSP > Servers > LSP-pyls`.

## Code Completion

This language server provides code completion through JEDI.

## Signature Help

This language server provides signature help through JEDI.

## Goto

This language server provides "goto definition" through JEDI.

## Find References

This language server provides "find references" through JEDI.

## Rename

This language server provides "rename word/symbol" through JEDI.

## Linters

The default linter is `pycodestyle`. The possible linters are:

- pycodestyle (`"pyls.plugins.pycodestyle.enabled"` in the settings)
- pydocstyle (`"pyls.plugins.pydocstyle.enabled"` in the settings)
- flake8 (`"pyls.plugins.flake8_lint.enabled"` in the settings)
  For flake8 to work, you must also modify `"pyls.configurationSources"` to be `["flake8"]` instead of the default
  `["pycodestyle"]`.
- pyflakes (`"pyls.plugins.pyflakes.enabled"` in the settings)
- pylint (`"pyls.plugins.pylint.enabled"` in the settings)
- mypy (`"pyls.plugins.pyls_mypy.enabled"` in the settings)

After changing a linter, you must restart Sublime Text.

## Formatters

The default formatter is `autopep8`. The possible formatters are:

- yapf (`"pyls.plugins.yapf.enabled"` in the settings)
- autopep8 (`"pyls.plugins.autopep8.enabled"` in the settings)
- black (`"pyls.plugins.pyls_black.enabled"` in the settings)

After changing a formatter, you must restart Sublime Text.

## Sorting import statements

To sort your import statements, you can enable `isort`. The relevant setting is `"pyls.plugins.pyls_isort.enabled"` in
the settings. Sorting is done through the "LSP: Format Document" option in the Context Menu by right-clicking in the
view with your mouse.

## Sublime Text Plugin Development

By default, the environment of pyls is adjusted so that the `PYTHONPATH` includes the directory where `sublime.py` and
`sublime_plugin.py` live, as well as the $DATA/Packages directory. This enables accurate code completion for these
files.
