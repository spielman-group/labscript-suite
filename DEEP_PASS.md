# labscript-suite deep pass

A planning document for the code-health campaign (`issues/code_health_campaign.md`
in the meta repo). It records what the pass leaves open and Ian's decisions, and
is deleted when the pass is done.

The repo is a metapackage and the suite's docs: one three-line Python file, no
tests.

## Open

- The pyproject dependency floors wait for campaign item 15.

## Decisions

- Ian's add-ons are not part of the suite and are not named here.
- Bitbucket is gone and is not referenced.
- The fork runs on PyQt6 only. Upstream's install docs recommend PySide6; a
  merge from `master` names PyQt6 instead (`pyqt6` on conda-forge), says it is
  the only binding, and warns against conda-forge's `pyqt`, which is PyQt5.
- Upstream's `.. todo::` notes in the docs stay.
