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
- **L2.** Ian: spielman-devices, labscript-agents and labscript-optimization are
  add-ons, not part of the suite, and are not named here. The README's
  labscript-optimization clone, editable install and examples sentence are gone.
  Outside this file, `git grep` finds none of the three names in the repo.
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
