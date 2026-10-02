# DSH plugins

Plugin index for the [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness)
(dsh) Web UI. Every plugin lives in its own repository; this repository only
holds the index.

## Plugins

| Plugin | What it adds | Repository |
| --- | --- | --- |
| **Everforest** | Six complete Everforest palettes (hard / medium / soft × dark / light) for the whole UI, with a depth picker in Settings → General | [dsh-theme-everforest](https://github.com/Frost-rA9/dsh-theme-everforest) |

## Install a plugin

1. Clone the plugin repository to a stable location — the profile links to that
   path, so moving the checkout later breaks the link:

   ```sh
   git clone https://github.com/Frost-rA9/dsh-theme-everforest
   ```

2. From a Harness session, install it into the active profile:

   ```
   plugin_manager install_bundle
     target: /absolute/path/to/dsh-theme-everforest
   ```

   The target must be the absolute path of the clone.

3. Or open the Plugin Manager page in the Web UI and point it at the same
   directory.

`install_bundle` performs the package installation and selects the bundle, so
the profile ends up depending on your checkout; `git pull` in the plugin
directory is then enough to update it. Each plugin's own README documents what
it needs and how to verify it.

## Adding a plugin to this index

A plugin listed here:

- is its own repository, named `dsh-<kind>-<name>` (for example
  `dsh-theme-everforest`);
- is an installable bundle: a `package.json` with `dsh.bundle.patch`, a
  `cordis.patch.yml` inserting its Loader rows, and — for UI plugins —
  `dsh.client` plus a `./client` export;
- ships display metadata so the Plugin Manager card is readable:
  `locale/en.json` and `locale/zh.json` with `meta.title` / `meta.description`,
  plus an `icon.svg`;
- declares only the dependencies it needs, and no install scripts;
- documents itself in `README.md` (add `README.zh.md` to mirror it in Chinese);
- uses [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
  for its history.

To list a new plugin, add a row to the table above and open a pull request.

## Repository layout

This index tracks only its own files: local plugin checkouts are separate git
repositories and are excluded by `.gitignore`.

## License

Index content is MIT licensed. Every plugin carries its own license.
