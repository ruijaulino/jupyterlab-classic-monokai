# Classic Monokai for JupyterLab 4

Charcoal notebook canvas (#1e1e1e), #282828 input cells, #232323 outputs, warm off-white text, lime headings and active-cell accents, olive selections, pink keywords, yellow strings, violet numbers, green definitions, and cyan builtins. Covers notebook and file editors, rendered Markdown, tables, prompts, menus, sidebars, tabs, search, and scrollbars.

## Install

Download the [installation ZIP](jupyterlab-classic-monokai-1.0.0-install.zip) (use GitHub's **Download raw file** button), extract the wheel, then open a terminal in the extracted folder. Requires JupyterLab 4 and Python 3.9 or later. This package has not been published to PyPI.

Run in the **same Python environment that launches JupyterLab**:

```sh
python -m pip install ./jupyterlab_classic_monokai-1.0.0-py3-none-any.whl
```

Restart JupyterLab, refresh the browser, then choose **Settings → Theme → Classic Monokai**. No Node.js or JupyterLab rebuild is needed. Keep the editor's theme setting on **jupyter** (the default), so CodeMirror uses the application palette.

The complete editable source (including prebuilt extension assets and example notebooks) is in [the source ZIP](jupyterlab-classic-monokai-1.0.0-source.zip). Download and unzip it, enter its folder, and run `python -m pip install .`. Prebuilt assets are included.

## Uninstall

Select another theme, then run:

```sh
python -m pip uninstall jupyterlab-classic-monokai
```

Restart JupyterLab and refresh the browser. Use `jupyter labextension list` to check discovery if the theme does not appear.

## Design and limits

Uses IThemeManager and JupyterLab's public CSS variables, including the CodeMirror 6 syntax variables. It does not patch editor internals or user settings. The theme stylesheet is removed when switching themes. No remote fonts, runtime requests, custom rendering engine, or extra editor dependencies.

The palette follows nbclassic/jupyterthemes Monokai; cyan builtins and pink tags lean toward Sublime Text. CodeMirror 6 tokenization differs from classic CodeMirror 5, so syntax coloring cannot be pixel-identical. Source Code Pro is preferred if installed, with system monospace fallbacks. Plots, images, third-party widgets and HTML with explicit inline colors retain their own styling. Exported standalone HTML/PDF does not automatically inherit this application theme.

## Customize / rebuild (maintainers only)

Edit `style/index.css`. The full upstream dark variable baseline in `style/base.css` avoids inheriting values from the previously selected theme.

```sh
python -m pip install build "jupyterlab==4.4.7"
npm ci
npm run build
python -m build
```

Then install the rebuilt wheel. The only JavaScript plugin registers the theme; the official JupyterLab builder creates the prebuilt extension.

For reproducible frontend builds, use JupyterLab 4.4.7 in a separate development environment before running `npm run build`. The npm lockfile pins the build dependencies; webpack is pinned to avoid a license-plugin incompatibility with newer webpack releases.

## References

- https://github.com/dunovank/jupyter-themes/blob/master/jupyterthemes/styles/monokai.less
- https://jupyterlab.readthedocs.io/en/stable/extension/extension_dev.html#theme-plugins
- https://github.com/jupyterlab/jupyterlab/blob/v4.4.7/packages/codemirror/src/theme.ts

See [VALIDATION.md](VALIDATION.md) for checks performed and a visual smoke-test checklist.


