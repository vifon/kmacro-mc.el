kmacro-x
========

A collection of Emacs commands, modes and functions building on top of
the keyboard macros (kmacros) system.

INSTALLATION
------------

`kmacro-x` is available on MELPA.  Example configuration with
`use-package`:

```elisp
(use-package kmacro-x
  :ensure t
  :init (kmacro-x-atomic-undo-mode 1)
  :bind (("C-<" . kmacro-x-mc-mark-previous)
         ("C->" . kmacro-x-mc-mark-next)))
```

FEATURES
--------

**kmacro-x-atomic-undo-mode**

While this mode is enabled, the kmacro executions can be undo-ed
atomically, as a single operation.  Often the user doesn't want to
undo a single step of a kmacro but rather the kmacro as a whole.

**kmacro-x-mc**

Emulates the typical multiple-cursors workflow using kmacros.
This way all the pitfalls of rolling a custom implementation of
multiple-cursors are avoided, while all the kmacro facilities, such as
counters, queries and kmacro editing, are gained virtually for free.

Usage:

1. `kmacro-x-mc-mark-next` and `kmacro-x-mc-mark-previous` are used to
   find the next/previous occurrence of the symbol at point (or the
   region if active) and create a fake cursor/selection at
   its position.
2. Some arbitrary actions are being performed.
3. `RET` can be used to apply the actions to all the other cursors or
   `C-g` can be used to abort the bulk operation.
