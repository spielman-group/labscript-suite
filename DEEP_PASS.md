# labscript-suite deep pass

A planning document for the code-health campaign (`issues/code_health_campaign.md`
in the meta repo). It records what the pass leaves open and Ian's decisions, and
is deleted when the pass is done.

The repo is a metapackage and the suite's docs: one three-line Python file, no
tests.

## Open

- The pyproject dependency floors wait for campaign item 15.

## Upstream stage

- Python 3.13 is the floor (Ian), in `requires-python`, the install docs and
  the Read the Docs build, which installs the metapackage.
- Upstream's `[programs]` section of the configuration page (`4d70063`) is
  adopted unchanged, since labscript-utils takes upstream's defaults
  (`4db2e74`).
- The metapackage lists no qtutils or zprocess, so their new floors are
  labscript-utils' to set.
- Upstream's docs commits to `5c97b66` are ported in `c167b8a`..`7c75e22`
  (`af83304`, `1645c5c`, `d7523ae`, then one fork commit). Adaptations: the Qt
  inventory comment names the fork's PyQt6 inventory; the developer install
  names PyQt6; the Bitbucket archive section and mention stay out; the
  configuration page names the TOML labconfig and its `[default]` section
  (`7c75e22`).
- Upstream's `d6a18b7` is not ported: it documents a `[gui] qt_binding`
  labconfig key, default PySide6, from labscript-utils #165, which the fork's
  labscript-utils lacks, and it contradicts PyQt6 only. It waits for Ian.

## Decisions

- Ian's add-ons are not part of the suite and are not named here.
- Bitbucket is gone and is not referenced.
- The fork runs on PyQt6 only. Upstream's install docs recommend PySide6; a
  merge from `master` names PyQt6 instead (`pyqt6` on conda-forge), says it is
  the only binding, and warns against conda-forge's `pyqt`, which is PyQt5.
- The docs follow upstream as closely as the fork allows (Ian).
