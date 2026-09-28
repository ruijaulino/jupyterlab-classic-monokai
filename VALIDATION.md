# Validation

Tested on Windows with Python 3.12 and JupyterLab 4.4.7.

- Official JupyterLab prebuilt extension build passed (webpack 5.99.9 pinned for builder compatibility).
- Python wheel built and installed in a fresh isolated environment.
- `jupyter labextension list` reported `jupyterlab-classic-monokai v1.0.0 enabled ok`.
- Browser inspection verified theme discovery, notebook and standalone Python syntax colors, rendered Markdown headings/inline code/links/tables, sidebar, active tabs, menu choices, prompts, stdout, stderr, edit-cell borders, and selected text.
- Switched Classic Monokai → JupyterLab Light → Classic Monokai: styles were removed and restored correctly.
- Uninstall succeeded; the extension disappeared from `jupyter labextension list`.

Targets JupyterLab >=4.0,<5; the entire minor-version/browser matrix has not been tested. Third-party widgets and pre-rendered plots may have their own colors.

For visual regression checks, open examples/Monokai-preview.ipynb and examples/sample.py. Check command mode, edit mode, selection, menus, Markdown preview, and a theme switch. The notebook has saved outputs so no kernel execution is needed.
