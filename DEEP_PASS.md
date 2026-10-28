# labscript-suite deep pass

A planning document for the code-health campaign (`issues/code_health_campaign.md`
in the meta repo). It records the pass's list and Ian's decisions, and is deleted
when the pass is done.

The repo is a metapackage and the suite's docs: one three-line Python file, no
tests.

## The list

- **C, contract.** No tests, so nothing to mark. Done.
- **L1.** The README cloned zprocess on `Production` and said it had no
  `Development`; it has one. Fixed: zprocess is cloned on `Development`.
  `desktop-app` has no `Development` and stays on `Production`.
- **L2.** Ian: his add-ons are not part of the suite and are not named here.
  The README's clone, editable install and examples sentence for one of them
  are gone, and `git grep` finds none of their names in the repo.
- **L3.** Ian resynced `master` with upstream (11 commits). Merged
  master → Production → Development → CodeHealth, keeping what is worth having
  (below).
- **L4.** `origin/maintenance/3.0.x` equals `upstream/maintenance/3.0.x`
  (`fba5b50`). To be deleted from origin; a push, so it waits for Ian's word.
- **L5.** The pyproject dependency floors are left for campaign item 15.
- **L6.** Upstream's `.. todo::` notes in the docs are left.
- **Step 2.6.** Nothing to do.

## Upstream's 11 commits

Kept:

- The install-doc rewrite: uv or pip into a virtual environment first, conda
  only with conda-forge and strict channel priority, and the conda caveats.
- The apparatus name must be a Python identifier.
- `git` installed in the developer conda environment.
- The release workflow sync.
- The README's install section, rewritten to match.

Dropped or changed:

- PySide6 as the recommended binding. The fork runs on PyQt6 only, so every
  install command names PyQt6 (`pyqt6` on conda-forge), and the paragraphs on
  the PyQt5 and PySide6 alternatives and `QT_ENV` say instead that PyQt6 is the
  only binding, and warn against conda's `pyqt`, which is PyQt5.
- The PySide6 6.12.0 crash warnings, which do not apply to PyQt6.

## Codex review

The merge resolution is sound. Eight documentation findings, each fixed:

1. The labconfig security examples were not valid TOML: an unquoted path and
   `True`. They are quoted, with lowercase `true`, as in the README.
2. Line continuations did not match the shell: Unix `\` in Windows cmd blocks,
   and cmd's `^` in the PowerShell blocks of the developer conda install. Each
   block now uses its own shell's character.
3. The developer conda install cloned before installing git, and the README's
   fork install assumed git. Both now install git into the environment first.
4. The README's fork install made its environment from the default channels.
   It now uses conda-forge throughout, as the install docs do. The old advice to
   install pyzmq from Anaconda, which contradicts the CurveZMQ guidance, is gone.
5. The docs build guide named `setup.cfg` files and recommonmark and m2r. It now
   names the `docs` extra of `pyproject.toml`.
6. It cloned an environment with `-c`; it is now `--clone`.
7. Dead links are repointed to live pages, or dropped where none exists, with
   the text kept: PCI 6251, Quicksyn FSW-0010 and the NovaTech blog post have no
   live page. Ian: Bitbucket is gone and is not referenced. The archive page,
   the README's archive section and its migration notes are removed, and the
   PineBlaster branch link points at GitHub.
8. This file named the add-ons; it no longer does.
